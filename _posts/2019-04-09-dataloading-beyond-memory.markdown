
---
layout: post
title:  "Data Loading Beyond the Memory Limit"
date:   2019-04-09 09:45:00 +0200
categories: ml
---

# Data Loading Beyond the Memory Limit


## Load Data and Save NumPy Arrays
1. get list of lists containing filenames from base directory
```
def get_list_of_files(base_dir):
  for type in ['sub_folder_1', 'sub_folder_2']:
    current_dir = join(base_dir, type)
    indiv_files = subfolders(current_dir)

    for file in indiv_files:
      indiv_dir = join(current_dir, file)
      data_file = join(...)
```
This does nothing more than crawling your data directory and returning a list of absolute file paths (check).

2. with the list of filename lists load the data as arrays
```
def load_and_preprocess(data_file, output_filename, output_folder):
  data = your_data_loading_function(data_file)
  data_npy = convert_to_numpy(data)

  # maybe perform some preprocessing here (crop to non-zero
  # regions, or more involved preprocessing even)

  original_shape = data_npy.shape

  # stack data arrays and cast to consistent data type
  data_npy = np.concatenate([i[None] for i in data_npy]).astype(np.float32)

  np.save(join(output_folder, output_filename) + '.npy', data_npy) #no need for memmap when saving, only when loading

  # add metadata, e.g. elements computed during preprocessing
  # which help in the analysis later on
  metadata = {'metadata_element1': ..., ...}

  save_pickle(metadata, join(output_folder, output_filename + '.pkl'))
```  

In main do:  
```
base_dir = '... absolute path'
list_of_lists = get_list_of_files(base_dir)
output_folder = 'some folder preferrably on SSD'
maybe_mkdir_output_folder(output_folder)

indiv_names = [i.split('/')[somewhere] for i in list_of_lists]
p = Pool(preprocesses = num_physical_cores)
p.starmap(load_and_preprocess, zip(list_of_lists, indiv_names, [output_folder] * len(list_of_lists)))
```
This function should load a given filename, optionally preprocess it, and save it as a NumPy file.  
Note that there are different strategies as for how to concatenate/stack your arrays which might be different from case to case.


## Note on Loading NumPy Arrays as Memmaps

```
np.load(file, mmap_mode='r')
```
This only reads parts of the array on the fly during training, which is very important if e.g. your patch size is smaller than the entire image. Make sure the NumPy files are stored in some folder on some SSD (HDDs and Network Drives might be too slow).


# Building a Data Loader
First we need some splitting of the dataset. We can do this on the basis of some dict keys.?
```
def get_list_of_individuals(preprocessed_data_folder):
  npy_files = subfiles(preprocessed_data_folder, suffix='.npy', join=False)

  individuals = [i[right_index] for i in npy_files]

  # get dataset splitting
  train_keys, test_keys = get_splitting_deterministic(individuals)
  return train_keys, test_keys
```
The actual data loader class (based on [MIC-DKFZ/batchgenerators](https://github.com/MIC-DKFZ/batchgenerators)):
```
class MyDataLoader(batchgenerators.dataloading.data_loader.DataLoader):
  def __init__(self, data, batch_size, patch_size, num_threads_in_multithreaded, seed_for_shuffle=123, return_incomplete=False, shuffle=True, infinite=True):
    super().__init__(data, batch_size, patch_size, num_threads_in_multithreaded, seed_for_shuffle, return_incomplete, shuffle, infinite)
    self.patch_size = patch_size
    self.indices = list(range(len(data)))

  def load_indiv(self, indiv):
    data = np.load(indiv+'.npy', mmap_mode='r')
    metadata = load_pickle(indiv+'.pkl')
    return data, metadata

  def generate_train_batch(self):
    indivs_for_batch = [self._data[i] for i in self.get_indices()]
    data = np.zeros((self.batch_size, self.num_modalities, *self.patch_size), dtype=np.float32)
    ground_truth = np.zeros((...))

    meta_data = []
    indiv_names = []

    for i, j in enumerate(patients_for_batch):
      data, metadata = self.load_indiv(j)
      # some more processing/augmentation here
      # split data in whatever way makes sense for you (data /ground truth, meta_data)
      indiv_names.append(j)
      meta_data.append(metadata)
      data[i] = data
      ground_truth[i] = some_part_of_data

    return {'data': data, 'ground_truth': ground_truth, 'metadata': meta_data, 'indiv_name': indiv_names}
```
