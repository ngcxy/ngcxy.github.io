---
layout: post
title: ML Accelerator DataFlow: Output Stationary in 3 approaches
date: 2024-03-18 00:00:00
description:
tags: Python Hardware-accelerator Data-flow Multi-thread
categories:
---

The Notebook of the post is provided on this [GitHub Link](https://github.com/ngcxy/Systems-of-ML)

In course USC EE-599:"Systems for Machine Learning", we learned three types of data-flow techniques often used in hardware accelerators:
weight stationary, input stationary, and output stationary.
In output stationary architecture, the output data remains stationary in the Processing Elements(PEs) while the input data and weights move.

In this post, I'll use Python to implement three approaches of output stationary data-flow - one from the textbook, and other two came up by myself.
We simulate PEs using the `Process` class from the `multiprocessing` library. Dataflows are managed via `Queue`, and outputs are stored in `Array`.

(Still editing...)