# ADKNet: Source-Adaptive Discriminative Kernels based Network for Remote Sensing Pansharpening
Homepage: https://liangjiandeng.github.io/

- Code for the paper: "Source-Adaptive Discriminative Kernels based Network for Remote Sensing Pansharpening", IJCAI, 2022.

- State-of-the-art (SOTA) performance for remote sensing pansharpening. Excellent generalization ability and low parameter number!

# Method
## Overall Structure

![ADKNet](show_image/adknet.png#pic_center)

The overall framework is a simple cascading structure primarily composed of several ADKGs.

## ADKG

![ADKG](show_image/adkg.png#pic_center)

The ADKG is composed of the spatial branch, the spectral branch, and the combination operation. The spatial branch extracts spatial details from PAN images, while the spectral branch captures spectral characteristics from LRMS images. Besides, the combination operation is applied to merge spatial and spectral information, generating discriminative kernels which are used for adaptive convolutions.

# Experimental Results

- Quantitative evaluation results on the WV3 dataset of pansharpening.

![wv3](show_image/wv3.png#pic_center)

- Quantitative evaluation results on the WV2 dataset of pansharpening (generalization capability).

![wv2](show_image/wv2.png#pic_center)

- Qualitative evaluation results on the WV2 dataset of pansharpening.

![wv2](show_image/wv2_visual.png#pic_center)

# Get Started
## Dataset
- The pansharpening datasets used in this paper are WV3 and WV2, which can be found on [this website](https://resources.maxar.com/). Due to the copyright of the datasets, we are unable to upload them. You can download the data and simulate it according to the simulation process in our paper. We recommend you process the datasets into the h5py format, otherwise the data loading section needs to be rewritten. After that, you can place the training dataset [here](ADKNet_for_pansharpening/training_data/), and the testing datasets [here](ADKNet_for_pansharpening/test_data/) folder.

- The HSISR (Hyper-Spectral Image Super-Resolution) datasets used in our paper are the CAVE and HARVARD, which can be found on [this website](https://github.com/J-FHu/Fusformer). After downloading the datasets, you can place the training dataset [here](ADKNet_for_HSISR/training_data/), and the testing datasets [here](ADKNet_for_HSISR/test_data/).

## Installation and Dependencies
```shell
git clone https://github.com/liangjiandeng/ADKNet.git
cd ADKNet
pip install -r requirements.txt
```

## Usage
- For pansharpening, we provide the model weight which is trained on the WV3 dataset for 275000 iterations, which can be found [here](ADKNet_for_pansharpening/Weights/). We have also provided some testing samples [here](ADKNet_for_pansharpening/test_data/).

- For HSISR, we provide the model weight which is trained on the CAVE dataset for around 125000 iterations, which can be found [here](ADKNet_for_HSISR/Weights/).

- For faster training and inference, you can install the [DDF operation](https://github.com/theFoxofSky/ddfnet), and uncomment the corresponding contents: line 135-163 in [this file](ADKNet_for_pansharpening/ADKG.py), line 4 in [this file](ADKNet_for_pansharpening/model.py), line 135-163 in [this file](ADKNet_for_HSISR/ADKG.py), and line 4 in [this file](ADKNet_for_HSISR/model.py).

```shell
# pansharpening train and test
cd ADKNet_for_pansharpening
python train.py
python test_single.py
python test_multi.py
# HSISR train and test
cd ..
cd ADKNet_for_HSISR
python train.py
python test_multi.py
```

# Citation
```
@inproceedings{ijcai2022p179,
  title     = {Source-Adaptive Discriminative Kernels based Network for Remote Sensing Pansharpening},
  author    = {Peng, Siran and Deng, Liang-Jian and Hu, Jin-Fan and Zhuo, Yuwei},
  booktitle = {Proceedings of the Thirty-First International Joint Conference on
               Artificial Intelligence, {IJCAI-22}},
  publisher = {International Joint Conferences on Artificial Intelligence Organization},
  editor    = {Lud De Raedt},
  pages     = {1283--1289},
  year      = {2022},
  month     = {7},
  note      = {Main Track},
  doi       = {10.24963/ijcai.2022/179},
  url       = {https://doi.org/10.24963/ijcai.2022/179},
}
```

# Contact
We are glad to hear from you. If you have any questions, please feel free to contact siran_peng@163.com.
