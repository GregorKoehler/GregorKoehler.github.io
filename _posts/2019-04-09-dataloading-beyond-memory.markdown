
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

  np.save(join(output_folder, output_filename) + '.npy', data_npy)

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
Note that there are different strategies as for how to
