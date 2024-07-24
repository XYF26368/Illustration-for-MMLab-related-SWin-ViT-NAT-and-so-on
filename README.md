# Illustration-for-MMLab-related-SWin-ViT-NAT-and-so-on
网上流传的各种用于分割的Transformer的pipeline都使用了mmseg, mmcv等一些库，这些库版本之间兼容性做得很差，并且由于Transformer模型源代码在上传之后基本没有更新，导致运行起来很困难。本文档将以分割任务为例，介绍如何运行使用了mmlab有关的库的pipeline。

## 1.第一步，找到mmsegmentation的官方库，并将其下载到自己的项目中，链接如下
https://github.com/open-mmlab/mmsegmentation

## 2.第二步，下载所需要的库
cd "the directory of mmsegmentation-main"
python setup.py build
python setup.py install
! 注意：mmcv里面有个很恶心的判定，你的版本既不能是最高的，也不能太低。个人建议选取比最高版本第一两个版本的即可，不然会报关于Assert的报错。
下载链接可参考：https://mmcv.readthedocs.io/en/latest/get_started/installation.html

## 3.第三步，更改配置文件信息
先找到tools文件夹，将其中的train.py文件第16行的配置文件信息代码改为： 
parser.add_argument('--config',default = "/mmsegmentation-main/configs/swin/swin-base-patch4-window7-in1k-pre_upernet_8xb2-160k_ade20k-512x512.py", help='train config file path')，其中我用的是swin所以用的swin的路径。想用别的网络的话，可以到路径/mmsegmentation-main/configs/里面寻找，或者把你自己编写的具有这个路径里面其他网络相似结构的网络传到这个路径下。

## 4.第四步，更改配置文件的数据路径
比如我使用ADE20K，那么我先找到/mmsegmentation-main/configs/_base_/datasets/ade20k.py 把里面的data_root路径改为你存放ADEChallengeData2016的路径即可。

## 5.第五步，运行训练
cd /mmsegmentation-main/tools 然后运行 python train.py即可。


# 引用
@misc{mmseg2020,
    title={{MMSegmentation}: OpenMMLab Semantic Segmentation Toolbox and Benchmark},
    author={MMSegmentation Contributors},
    howpublished = {\url{https://github.com/open-mmlab/mmsegmentation}},
    year={2020}
}
