
## Overview
Pytorch code of ECE4880 project, Hybrid Image Compression model with Transformer and CNN.


## Content

- [Prerequisites](#prerequisites)
- [Data Preparation](#data-preparation)
- [Training](#training)

## Prerequisites

You should install the libraries of this repo.

```
pip install -r requirements.txt
```

## Data Preparation

The validation data is the popular kodak dataset.
```
bash data/download_kodak.sh
```

## Training

For high birate training:

```bash
CUDA_VISIBLE_DEVICES=0 python train.py --config example/config_swin_8192.json -n name --train training_set_path --val Kodak_path --pretrain pretrain_path
```

For low bitrate training:

```bash
CUDA_VISIBLE_DEVICES=0 python train.py --config example/config_swin_2048.json -n name --train training_set_path --val Kodak_path --pretrain pretrained_model_path
```



## Testing

#### PSNR and MS-SSIM experiments 

For high bitrate of 8192, we can test it as follows.

```bash
CUDA_VISIBLE_DEVICES=0 python compression/test.py --config example/config_swin_8192.json -n name -t kodak -p pretained_model_path  --val Kodak_path
```




## Acknowledgement
The codes are heavily based on [Swin-Transformer](https://github.com/microsoft/Swin-Transformer) and [compression](https://github.com/liujiaheng/compression).


