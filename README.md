This experiment tries to replicate the paper [Depth Pruning with Auxiliary Networks for TinyML](https://arxiv.org/abs/2204.10546) .
This experiment uses the CIFAR-10 dataset resized to 224x224 on MobileNet V1.
The Pruned Network is trained with values initialized from the original network and with random initialization.
![Pruning](https://github.com/rrquizon1/Depth-Pruning-Replication/assets/70574862/9786bac8-1112-4018-9fe2-ceea8863e2ac)

Results show that for CIFAR-10 dataset, even with random initialization, the pruned network shows competitive performance compared to the original netowrk. 

With original network having 3.2M parameters with 89.73% accuracy and the pruned networks reduced to only 310k parameters with 88.80% (initialized values from original network) and 88.68% (random initialization) accuracy. This shows an effective pruning with around 90% reduction with less than 1 % reduction in accuracy.
This reduction decreases memory requirements of the model and could potentially speed up inference.

The Implementation of MobileNetV1 used in this experiment is from here: [Implement MobileNet-v1 in PyTorch](https://medium.com/@karuneshu21/implement-mobilenet-v1-in-pytorch-fd03a6618321)
