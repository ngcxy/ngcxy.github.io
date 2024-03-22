---
layout: post
title:  "ML Accelerator DataFlow: Output Stationary in 3 approaches"
date: 2024-03-18 00:00:00
description:
tags: Python Hardware-accelerator Data-flow Multi-thread
categories:
---

> The Notebook of the post is provided in this [GitHub Link](https://github.com/ngcxy/Systems-of-ML)

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/3/header.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

- image from EE-599 slides


In course [USC EE-599:"Systems for Machine Learning"](https://ece-classes.usc.edu/ee599ml/), we learned three types of data-flow techniques often used in hardware accelerators:
weight stationary, input stationary, and output stationary.
In output stationary architecture, the output data remains stationary in the Processing Elements(PEs) while the input data and weights move.

In this post, I'll use Python to implement three approaches of 1D output stationary dataflow - one from the textbook, and other two came up by myself.
I simulate PEs using the `Process` class from the `multiprocessing` library. Dataflows are managed via `Queue`, and outputs are stored in `Array`.

### A short summary first

All three approaches pass the validation, the other two dataflows achieve a slightly **faster runtime** than the first one.
There is also an advantage of the other two that they **don't need extra buffer** to store the values.
(The input feature map size is 64; the weight size is 4)

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/3/res.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

---

### Output Stationary 1 - textbook example

The weights are broadcast while activations(i.e., input feature map) are passed through the PEs sequentially.

Notice that the PEs only retrieve weights when the required activations are passed in. Before that, the weights will be stored in the buffer of the queues.

(For the figure on the right, notice that 0, 1, 2... are just index, not real number)

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/3/os1.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


We can observe that in this case each PE needs to store the weight for a long time until the corresponding input is passed in,
which in my point of view might not be an efficient way.

### Output Stationary 2

In this new approach, we try simply switching the dataflow of the weights and activations. The activations are broadcast while weights are passed through the PEs sequentially.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/3/os2.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

In this case, we no longer need to store any values in PE. The process is more straight-forward, and the runtime is also a bit faster.

### Output Stationary 3

In this new approach, the weights are broadcast while activations are passed through the PEs sequentially.

This is a special case where the IDs of the PEs in this approach are arranged in a reversed order.
Also, all PEs will not start retrieving the broadcast weight until a certain time_step (when the first activation arrives at the last PE).

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/3/os3.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This method also avoids the storing issue, and achieves the highest efficiency among all.