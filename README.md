# BGNN
This is the TensorFlow implementation of our paper accepted by IJCAI 2020:

>Hongmin Zhu, Fuli Feng, Xiangnan He, Xiang Wang, Yan Li, Kai Zheng, Yongdong Zhang, Bilinear Graph Neural Network with Neighbor Interactions. [Paper in arXiv](https://arxiv.org/abs/2002.03575).

## Introduction
We propose a new graph convolution operator, augmenting the weighted sum with pairwise interactions of the representations of neighbor nodes. We specify two BGNN models named BGCN and BGAT, based on the well-known GCN and GAT, respectively.

## Dependencies
The code is tested by server with RTX 1080Ti running in a docker container which includes the following packages:
* python 3.6.3
* tensorflow 1.4.0
* numpy 1.13.3
* scipy 1.0.0
* networkx 2.0

In addition, CUDA 8 and cuDNN 6 have been used.

## Simulation example
Here are the instruction commands for running the codes on Citeseer in a docker container. 
### 1-layer BGCN-A
* Command
```
cd BGCN/1-layer/BGCN-A/
python gcn.py --model bgcn --dropout 0.0 --weight_decay 5e-4 --alpha 0.9 --epochs 2000 --learning_rate 0.005
```
* Output
```
Epoch: 0001 train_loss= 1.79177 train_acc= 0.1250 val_loss= 1.79168 val_acc= 0.2840 tst_loss= 1.79169 tst_acc= 0.2600 time= 0.112
Epoch: 0002 train_loss= 1.79154 train_acc= 0.5250 val_loss= 1.79162 val_acc= 0.3820 tst_loss= 1.79162 tst_acc= 0.3660 time= 0.055
...
Epoch: 1999 train_loss= 1.52770 train_acc= 0.8333 val_loss= 1.67561 val_acc= 0.6460 tst_loss= 1.67752 tst_acc= 0.6940 time= 0.049
Epoch: 2000 train_loss= 1.52768 train_acc= 0.8333 val_loss= 1.67560 val_acc= 0.6460 tst_loss= 1.67750 tst_acc= 0.6940 time= 0.048
test_loss= 1.69706 test_acc= 0.7010
early stop #epoch 1004 val_loss= 1.69771 val_acc= 0.6820
```
### 1-layer BGCN-T
* Command
```
cd BGCN/1-layer/BGCN-T/
python gcn.py --model bgcn --dropout 0.0 --weight_decay 5e-4 --alpha 0.7 --epochs 2000 --learning_rate 0.005
```
* Output
```
Epoch: 0001 train_loss= 1.79160 train_acc= 0.2083 val_loss= 1.79143 val_acc= 0.2900 tst_loss= 1.79137 tst_acc= 0.2910 time= 0.150
Epoch: 0002 train_loss= 1.79057 train_acc= 0.6333 val_loss= 1.79115 val_acc= 0.3380 tst_loss= 1.79107 tst_acc= 0.3910 time= 0.071
...
Epoch: 1999 train_loss= 1.57680 train_acc= 0.8583 val_loss= 1.69943 val_acc= 0.6600 tst_loss= 1.69793 tst_acc= 0.6930 time= 0.058
Epoch: 2000 train_loss= 1.57679 train_acc= 0.8583 val_loss= 1.69942 val_acc= 0.6600 tst_loss= 1.69792 tst_acc= 0.6930 time= 0.064
test_loss= 1.71482 test_acc= 0.7080
early stop #epoch 893 val_loss= 1.71812 val_acc= 0.6860
```
## Dataset
We utilize three benchmark datasets of citation network---Pubmed, Cora and Citeseer.
