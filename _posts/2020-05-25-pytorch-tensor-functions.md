---
title: 'Exploring Tensor functions in Pytorch'
collection: posts
type: "Blog Posts"
date: 2020-05-25
permalink: /posts/2020/0-GAN/tensor-functions-pytorch/
tags:
  - Pytorch
  - Tensor
  - Functions
---

I am fairly comfortable building Deep Neural Networks (DNN) with [Keras](https://keras.io/) library and infact I built a CNN model - [Plantmd](https://github.com/upendrak/plantmd) to predict plant diseases as part of [Insight](http://insightdatascience.com/) Data Science fellowship program. However as people often say, it's always important to learn a new language/program to see how it differs from the language/program that you are comfortable. So with this in mind, I have decided to take spend time to do the exciting [Deep Learning with PyTorch: Zero to GANs](https://jovian.ml/forum/c/pytorch-zero-to-gans/18) workshop on [Jovian.ml](http://jovian.ml/).

As part of the first assignment, we were asked to pick out five `torch.Tensor` functions in Pytorch and use them with examples. So here are my five 'torch.Tensor` functions.

* torch.as_tensor()
* torch.arange()
* torch.reshape()
* torch.abs()
* torch.is_leaf()

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=1" title="Jovian Viewer" height="113" width="800" frameborder="0" scrolling="auto"></iframe>

## 1. torch.as_tensor()

In Pytorch the recommended way to build tensors are either using `torch.tensor()` and `torch.as_tensor()`. So what is the difference? `torch.tensor()` always copies the data whereas `torch.as_tensor()` always tries to avoid copies of the data. This is especially useful if you have a `numpy` array and want to avoid copying the `numpy` array into a tensor.

### 1.1 Let's understand this by creating a `numpy` array first

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=3" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

### 1.2 Create a tensor using `torch.tensor()` function

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=4" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

### 1.3 Create a tensor using `torch.as_tensor()` function

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=5" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

As you can see, there is no difference in the outputs between `torch.tensor(arr)` or `torch.as_tensor(arr)`

### 1.4 Now let's create a sligtly complicated `numpy` array

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=10" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=11" title="Jovian Viewer" height="249" width="800" frameborder="0" scrolling="auto"></iframe>

The tensor creation failed with `torch.as_tensor()` function here because the `numpy` array that was created is a 2-D array with rows that have different lengths which works for `numpy` arrays but fails during conversion from `numpy` to a `tensor`.

To summarize, `torch.tensor()` copies the `numpy` array whereas `torch.as_tensor()` shares the memory with the `numpy` array

## 2. torch.arange()

This function returns a 1-D tensor of size (end-start/step) with values from the intervals start, end taken with common difference `step` from `start`.

### 2.1 Let's first create a tensor

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=15" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

In the above example, `torch.arange()` function returns numbers 0, 1, 2, 3, 4, 5 with an interval of 1. Instead of specifiying the start (the default is 0) and the step size (the default is 1), you can just give the end number (in this example 5) and `torch.arange()` will generate numbers 0-5 similar to example 1.

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=17" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

### 2.2 Now let's see an example where things can go wrong

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=19" title="Jovian Viewer" height="245" width="800" frameborder="0" scrolling="auto"></iframe>

In this example, the function assumes that start is 0, end is -5 and step size is 1 and it is not able to return the numbers from 0, -5 with a step size of 1. This can be fixed by giving an upper bound (for example 0).

To summarize `torch.arange()` is a very convenient function to generate a sequence of numbers from `start` to `end` with a user specified `step` size.

## 3. torch.reshape()

This function returns a `tensor` with the same data and number of elements as `input` but with the specified shape.

### 3.1 Let's see this with an example

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=23" title="Jovian Viewer" height="184" width="800" frameborder="0" scrolling="auto"></iframe>

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=24" title="Jovian Viewer" height="191" width="800" frameborder="0" scrolling="auto"></iframe>

As can be seen in the above example, `torch.reshape()` has returned a tensor with the same data but with a specified shape of `2 x 2` for earlier shape of `1 * 4`.

What if you want to convert the `input` tensor of shape `4 x 1` into an array of `1 x 4`, then you can just specify `(-1, 1)` as shown in this example. Infact you can leave the second number and just specify `(-1,)`

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=26" title="Jovian Viewer" height="256" width="800" frameborder="0" scrolling="auto"></iframe>

### 3.2 Specifying wrong reshape parameter

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=28" title="Jovian Viewer" height="245" width="800" frameborder="0" scrolling="auto"></iframe>

This is the frequent mistake that people often do with `torch.reshape()` function. The above error indicates that the original input is a size of `4 x 1` whereas, we ask it to generate a tensor of shape `2 x 3` which is not possible. This is because `2 x 3 = 6` whereas the original size is `4 x 1 = 4`.

To summarize, reshaping a tensor using `torch.reshape()` is quite important in matrix multiplication and other functionalities.


## 4. torch.abs()

The function `torch.abs()` computes element wise absolute value of an `input` tensor.

### 4.1 Let's see an simple example

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=32" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=33" title="Jovian Viewer" height="119" width="800" frameborder="0" scrolling="auto"></iframe>

As can be seen, `torch.abs()` was able to convert all the negative values into positive values from an `input` tensor consisting of 3 elements.

`torch.abs()` not only works on the 1-D tensor but also can also work on 2-D tensors such as matrices as show in this example.

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=35" title="Jovian Viewer" height="157" width="800" frameborder="0" scrolling="auto"></iframe>

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=36" title="Jovian Viewer" height="157" width="800" frameborder="0" scrolling="auto"></iframe>

### 4.2 Using `torch.abs()` on a wrong tensor type 

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=38" title="Jovian Viewer" height="245" width="800" frameborder="0" scrolling="auto"></iframe>

The error here indicates the the `torch.abs()` only works on tensors that have numbers (floats, integers etc.,) and not on boolean values (TRUE/FALSE, Yes/No etc.,). So make sure to check the tensor type before using `torch.abs()` function.

To summarize `torch.abs()` is a nice little functionality in Pytorch that returns the absolute value of a numerical tensor that is of any dimension.


## 5. torch.is_leaf()

A `leaf` node/variable is a variable that is at the beginning of the graph. That means that no operation is tracked by the `autograd` engine created it. All tensors that have `requires_grad` set to False will be leaf tensors by convention.

### 5.1 Let's understand this with an example

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=42" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

Here the `a` tensor is a leaf variable

Let's create another example where a tensor is not a leaf variable. 

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=44" title="Jovian Viewer" height="136" width="800" frameborder="0" scrolling="auto"></iframe>

As can be seen in the above example, the tensor `b` was not created by the user but was created by an operation that cast a float tensor into a double tensor. So the tensor `b` is not a leaf variable.

### 5.2 Creating a tensor with gradient that has wrong data type

In this example, we tried to check if the tensor is a leaf variable or not, but before we can check that out, we get an error as shown here.

<iframe src="https://jovian.ml/embed?url=https://jovian.ml/upendrakumar-devisetty/01-tensor-operations/v/4&cellId=46" title="Jovian Viewer" height="245" width="800" frameborder="0" scrolling="auto"></iframe>

If you want to create gradients for an tensor, floating point data type are only acceptable. So make sure you fix that before you can use `is_leaf()` function.

To summarize `is_leaf()` is a convenient function to check if the variable is at the beginning of the graph or not so that you don't have to keep a track of it manually.

## Conclusion

This notebook explores five Tensor functions in Pytorch with detailed examples including the cases where things go wrong. Understanding Tensor functions in Pytroch is very important so that they can be applied correctly in downstream analysis. 

If you want to try these functions by yourself, visit this [notebook](https://jovian.ml/upendrakumar-devisetty/01-tensor-operations), fork/clone and press Run.

## Reference Links

* Official documentation for [torch.Tensor](https://pytorch.org/docs/stable/tensors.html)

* My Jovian [notebook](https://jovian.ml/upendrakumar-devisetty/01-tensor-operations)

* [Jovian ML](https://jovian.ml)