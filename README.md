# FSRCNN-PyTorch

## Overview

This repository contains an op-for-op PyTorch reimplementation of [Accelerating the Super-Resolution Convolutional Neural Network](https://arxiv.org/abs/1608.00367v1).

## Table of contents

- [FSRCNN-PyTorch](#fsrcnn-pytorch)
    - [Overview](#overview)
    - [Table of contents](#table-of-contents)
    - [About Accelerating the Super-Resolution Convolutional Neural Network](#about-accelerating-the-super-resolution-convolutional-neural-network)
    - [Download weights](#download-weights)
    - [Download datasets](#download-datasets)
        - [Download train dataset](#download-train-dataset)
        - [Download valid dataset](#download-valid-dataset)
    - [Test](#test)
    - [Train](#train)
    - [Result](#result)
    - [Credit](#credit)
        - [Accelerating the Super-Resolution Convolutional Neural Network](#accelerating-the-super-resolution-convolutional-neural-network)

## About Accelerating the Super-Resolution Convolutional Neural Network

If you're new to FSRCNN, here's an abstract straight from the paper:

As a successful deep model applied in image super-resolution (SR), the Super-Resolution Convolutional Neural Network (
SRCNN) has demonstrated superior performance to the previous hand-crafted models either in speed and restoration
quality. However, the high computational cost still hinders it from practical usage that demands real-time performance (
24 fps). In this paper, we aim at accelerating the current SRCNN, and propose a compact hourglass-shape CNN structure
for faster and better SR. We re-design the SRCNN structure mainly in three aspects. First, we introduce a deconvolution
layer at the end of the network, then the mapping is learned directly from the original low-resolution image (without
interpolation) to the high-resolution one. Second, we reformulate the mapping layer by shrinking the input feature
dimension before mapping and expanding back afterwards. Third, we adopt smaller filter sizes but more mapping layers.
The proposed model achieves a speed up of more than 40 times with even superior restoration quality. Further, we present
the parameter settings that can achieve real-time performance on a generic CPU while still maintaining good performance.
A corresponding transfer strategy is also proposed for fast training and testing across different upscaling factors.

## Download weights

- [Google Driver](https://drive.google.com/drive/folders/1-Cp0UVqSLBvW-gNV_Xvw5hlj1Ph7f6Oc?usp=sharing)
- [Baidu Driver](https://pan.baidu.com/s/1mXzvJeHQtSQxmhbBHQYcnA) access:`llot`

## Download datasets

### Download train dataset

#### TG191

- Image format
    - [Baidu Driver](https://pan.baidu.com/s/1JsbkfoZqB6HdCBDBS3DOrw) access: `llot`

- LMDB format (train)
    - [Baidu Driver](https://pan.baidu.com/s/1eqeORnKcTmGatx2kAG92-A) access: `llot`

- LMDB format (valid)
    - [Baidu Driver](https://pan.baidu.com/s/1W34MeEtLY0m-bOrnaveVmw) access: `llot`

### Download valid dataset

#### Set5

- Image format
    - [Google Driver](https://drive.google.com/file/d/1GtQuoEN78q3AIP8vkh-17X90thYp_FfU/view?usp=sharing)
    - [Baidu Driver](https://pan.baidu.com/s/1dlPcpwRPUBOnxlfW5--S5g) access:`llot`

#### Set14

- Image format
    - [Google Driver](https://drive.google.com/file/d/1CzwwAtLSW9sog3acXj8s7Hg3S7kr2HiZ/view?usp=sharing)
    - [Baidu Driver](https://pan.baidu.com/s/1KBS38UAjM7bJ_e6a54eHaA) access:`llot`

#### BSD200

- Image format
    - [Google Driver](https://drive.google.com/file/d/1cdMYTPr77RdOgyAvJPMQqaJHWrD5ma5n/view?usp=sharing)
    - [Baidu Driver](https://pan.baidu.com/s/1xahPw4dNNc3XspMMOuw1Bw) access:`llot`

## Test

Modify the contents of the file as follows.
- line 24: `upscale_factor` change to the magnification you need to enlarge. 
- line 25: `mode` change Set to valid mode.
- line 75: `model_path` change weight address after training.

## Train

Modify the contents of the file as follows.
- line 24: `upscale_factor` change to the magnification you need to enlarge. 
- line 25: `mode` change Set to train mode.

If you want to load weights that you've trained before, modify the contents of the file as follows.
- line 46: `resume` change to `True`. 
- line 47: `strict` Transfer learning is set to `False`, incremental learning is set to `True`.
- line 48: `start_epoch` change number of training iterations in the previous round.
- line 49: `resume_weight` the weight address that needs to be loaded.

## Result

Source of original paper results: https://arxiv.org/pdf/1501.00092v3.pdf

In the following table, the value in `()` indicates the result of the project, and `-` indicates no test.

| Dataset | Scale |       PSNR       |
| :-----: | :---: | :--------------: |
|  Set5   |   2   | 36.94(**36.94**) |
|  Set5   |   3   | 33.06(**32.88**) |
|  Set5   |   4   | 30.55(**30.58**) |

Low Resolution / Super Resolution / High Resolution
<span align="center"><img src="assets/result.png"/></span>

## Credit

### Accelerating the Super-Resolution Convolutional Neural Network

_Chao Dong, Chen Change Loy, Xiaoou Tang_ <br>

**Abstract** <br>
As a successful deep model applied in image super-resolution (SR), the Super-Resolution Convolutional Neural Network (
SRCNN) has demonstrated superior performance to the previous hand-crafted models either in speed and restoration
quality. However, the high computational cost still hinders it from practical usage that demands real-time performance (
24 fps). In this paper, we aim at accelerating the current SRCNN, and propose a compact hourglass-shape CNN structure
for faster and better SR. We re-design the SRCNN structure mainly in three aspects. First, we introduce a deconvolution
layer at the end of the network, then the mapping is learned directly from the original low-resolution image (without
interpolation) to the high-resolution one. Second, we reformulate the mapping layer by shrinking the input feature
dimension before mapping and expanding back afterwards. Third, we adopt smaller filter sizes but more mapping layers.
The proposed model achieves a speed up of more than 40 times with even superior restoration quality. Further, we present
the parameter settings that can achieve real-time performance on a generic CPU while still maintaining good performance.
A corresponding transfer strategy is also proposed for fast training and testing across different upscaling factors.

[[Paper]](https://arxiv.org/pdf/1608.00367v1.pdf)

```bibtex
@article{DBLP:journals/corr/DongLT16,
  author    = {Chao Dong and
               Chen Change Loy and
               Xiaoou Tang},
  title     = {Accelerating the Super-Resolution Convolutional Neural Network},
  journal   = {CoRR},
  volume    = {abs/1608.00367},
  year      = {2016},
  url       = {http://arxiv.org/abs/1608.00367},
  eprinttype = {arXiv},
  eprint    = {1608.00367},
  timestamp = {Mon, 13 Aug 2018 16:47:56 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/DongLT16.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
