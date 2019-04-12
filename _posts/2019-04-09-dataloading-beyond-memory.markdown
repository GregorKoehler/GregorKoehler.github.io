
---
layout: post
title:  "Data Loading Beyond the Memory Limit"
date:   2019-02-20 08:45:27 +0200
categories: tech ml
---

# Data Loading Beyond the Memory Limit





Recently, a few (2) friends of mine started using [PyTorch](www.pytorch.org). PyTorch offers great tutorials to get you started, but in my opinion there's a specific order to go through the tutorials and additional non-official material which minimizes the confusion when getting started with PyTorch. Just to be clear, in my humble opinion PyTorch is currently (still holds in 2019) the most intuitive Deep Learning framework out there, but why not try to make things even more smooth?

So without further ado, here's my preferred order of materials to get easy the way into PyTorch-land!

0. [What is PyTorch?](https://pytorch.org/tutorials/beginner/blitz/tensor_tutorial.html#sphx-glr-beginner-blitz-tensor-tutorial-py)
  * basic intro showing the relation between PyTorch tensors and NumPy arrays
  * also introduces the notion of the `torch.device` and how to move tensors to/from GPU
1. [Autograd - Automatic Differentiation](https://pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html#sphx-glr-beginner-blitz-autograd-tutorial-py)
  * introduces `autograd`, best read in conjunction with [notes on autograd mechanics](https://pytorch.org/docs/stable/notes/autograd.html)
2. [What is torch.nn, really?](https://pytorch.org/tutorials/beginner/nn_tutorial.html)
  * great walk-through of multiple levels of PyTorch abstraction in the setting of a basic MNIST example
3. [Grokking PyTorch](https://github.com/Kaixhin/grokking-pytorch)
  * again, an MNIST example, but with explanations which nicely complement the one in `2.`

to be continued...
