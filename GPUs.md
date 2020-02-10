

Available GPUs
==============

![Image of create bucket](imgs/Screen%20Shot%202020-02-10%20at%2012.32.09%20AM.png?raw=true)


Creating a Jupyter Notebook with GPUs
=====================================

![Image of create bucket](imgs/Screen%20Shot%202020-02-10%20at%2012.31.39%20AM.png?raw=true)






When to use TPUs

Cloud TPUs are optimized for specific workloads. In some situations, you might want to use GPUs or CPUs on Compute Engine instances to run your machine learning workloads. In general, you can decide what hardware is best for your workload based on the following guidelines:

CPUs

Quick prototyping that requires maximum flexibility
Simple models that do not take long to train
Small models with small effective batch sizes
Models that are dominated by custom TensorFlow operations written in C++
Models that are limited by available I/O or the networking bandwidth of the host system
GPUs

Models that are not written in TensorFlow or cannot be written in TensorFlow
Models for which source does not exist or is too onerous to change
Models with a significant number of custom TensorFlow operations that must run at least partially on CPUs
Models with TensorFlow ops that are not available on Cloud TPU (see the list of available TensorFlow ops)
Medium-to-large models with larger effective batch sizes
TPUs

Models dominated by matrix computations
Models with no custom TensorFlow operations inside the main training loop
Models that train for weeks or months
Larger and very large models with very large effective batch sizes
Cloud TPUs are not suited to the following workloads:

Linear algebra programs that require frequent branching or are dominated element-wise by algebra. TPUs are optimized to perform fast, bulky matrix multiplication, so a workload that is not dominated by matrix multiplication is unlikely to perform well on TPUs compared to other platforms.
Workloads that access memory in a sparse manner might not be available on TPUs.
Workloads that require high-precision arithmetic. For example, double-precision arithmetic is not suitable for TPUs.
Neural network workloads that contain custom TensorFlow operations written in C++. Specifically, custom operations in the body of the main training loop are not suitable for TPUs.
Neural network workloads must be able run multiple iterations of the entire training loop on the TPU. Although this is not a fundamental requirement of TPUs themselves, this is one of the current constraints of the TPU software ecosystem that is required for efficiency.




https://cloud.google.com/tpu/pricing

https://cloud.google.com/tpu/docs/tpus
