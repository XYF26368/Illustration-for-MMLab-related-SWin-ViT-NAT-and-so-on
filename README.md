# Illustration-for-MMLab-related-SWin-ViT-NAT-and-so-on
网上流传的各种用于分割的Transformer的pipeline都使用了mmseg, mmcv等一些库，这些库版本之间兼容性做得很差，并且由于Transformer模型源代码在上传之后基本没有更新，导致运行起来很困难。本文档将以分割任务为例，介绍如何运行使用了mmlab有关的库的pipeline。

## 1.第一步，找到mmsegmentation的官方库，并将其下载到自己的项目中，链接如下
https://github.com/open-mmlab/mmsegmentation

## 2.第二步，下载所需要的库
cd "the directory of mmsegmentation-main"\n
python setup.py build\n
python setup.py install\n
! 注意：mmcv里面有个很恶心的判定，你的版本既不能是最高的，也不能太低。个人建议选取比最高版本第一两个版本的即可，不然会报关于Assert的报错。
下载链接可参考：https://mmcv.readthedocs.io/en/latest/get_started/installation.html

## 3.第三步，
