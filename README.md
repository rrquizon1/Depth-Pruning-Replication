This experiment tries to replicate the paper [Depth Pruning with Auxiliary Networks for TinyML](https://arxiv.org/abs/2204.10546) .

## CIFAR-10 Results
This experiment uses the CIFAR-10 dataset resized to 224x224 on MobileNet V1.
The Pruned Network is trained with values initialized from the original network and with random initialization.
![image](https://github.com/user-attachments/assets/edcc1381-4fd9-4f85-bdc4-427d663bb8df)
Results show that for CIFAR-10 dataset, even with random initialization, the pruned network shows competitive performance compared to the original netowrk. 

With original network having 3.2M parameters with 89.73% accuracy and the pruned networks reduced to only 310k parameters with 88.80% (initialized values from original network) and 88.68% (random initialization) accuracy. This shows an effective pruning with around 90% reduction with less than 1 % reduction in accuracy.
This reduction decreases memory requirements of the model and could potentially speed up inference.

## Imagenette and Imagewoof Results
In addition to CIFAR-10, this setup was also tested with Imagenette and Imagewoof, which are subsets of the ImageNet dataset. These datasets have higher resolutions than CIFAR-10 but contain fewer images. You can refer to the dataset for more details:https://github.com/fastai/imagenette

Using these two datasets I got some interesting results. See below for the results:
![image](https://github.com/user-attachments/assets/45417884-1012-4e25-81cc-18d7016830f6)
![image](https://github.com/user-attachments/assets/d81f9d3b-0491-48b7-aeed-3e9e35d84fb6)


Using these two datasets, I noted an increase in accuracy after pruning the network and initializing the pruned network's weights from the pre-trained original network. For the Imagenette dataset, the pruned network's accuracy rose from 76.50% to 81.15%. For the Imagewoof dataset, there was a 7.68% increase, with the original network at 55.94% accuracy and the pruned network at 63.62%. This is significant as it demonstrates improved performance rather than degradation after pruning blocks which has 90% parameter reduction from 3.2M to 310k. From these results, we can observe two things regarding pruning:

*  Pruning can act as regularization, preventing overfitting and improving accuracy in the network depending on the datasets it is used. This was not observed in the original paper, which used a keyword spotting dataset and on my previous experiment on CIFAR-10.
*  Initialization values are crucial. The results show that randomly initializing the network's values leads to some improvement, but using values from the original pre-trained network results in a more significant improvement.


## Reference Mobilenet V1 implementation
The Implementation of MobileNetV1 used in this experiment is from here: [Implement MobileNet-v1 in PyTorch](https://medium.com/@karuneshu21/implement-mobilenet-v1-in-pytorch-fd03a6618321)
