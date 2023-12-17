# MIMDepth
This is the official code for [ICRA 2023](https://www.icra2023.org) paper 
[Image Masking for Robust Self-Supervised Monocular Depth Estimation](https://arxiv.org/abs/2210.02357) by
[Hemang Chawla](https://scholar.google.com/citations?user=_58RpMgAAAAJ&hl=en&oi=ao),
[Kishaan Jeeveswaran](https://scholar.google.nl/citations?user=JcqW3_QAAAAJ&hl=en&oi=ao), 
[Elahe Arani](https://scholar.google.nl/citations?user=e_I_v6cAAAAJ&hl=en&oi=ao) and 
[Bahram Zonooz](https://scholar.google.com/citations?hl=en&user=FZmIlY8AAAAJ).

![alt text](assets/MIMDepth.png "MIMDepth")

We propose MIMDepth, a method that adapts masked image modeling (MIM) for self-supervised monocular depth estimation

## Install

MIMDepth was trained on TeslaV100 GPU for 20 epochs with AdamW optimizer at a resolution of (192 x 640) with a 
batchsize 12. The docker environment used can be setup as follows:

```
git clone https://github.com/NeurAI-Lab/MIMDepth.git
cd MIMDepth
make docker-build
```

## Training
MIMDepth is trained in a self-supervised manner from videos. 
For training, utilize a `.yaml` config file or a `.ckpt` model checkpoint file with `scripts/train.py`.
```
python scripts/train.py <config_file.yaml or model_checkpoint.ckpt>
```
Example [config file](configs/train_kitti_mimdepth_pt.yaml) to train MIMDepth can be found in [configs](configs) folder. 

## Evaluation
A trained model can be evaluated by providing a `.ckpt` model checkpoint.
```
python scripts/eval.py --checkpoint <model_checkpoint.ckpt>
```

For running inference on a single image or folder, 
```
python scripts/infer.py --checkpoint <checkpoint.ckpt> --input <image or folder> --output <image or folder> [--image_shape <input shape (h,w)>]
```

Pretrained Models for MT-SfMLearner and MIMDepth can be found 
[here](https://drive.google.com/drive/folders/17igYTKh0WG1EZw93NiJd5tUN3gcSY-rj?usp=sharing).

## Cite Our Work
If you find the code useful in your research, please consider citing our paper:
<pre>
@inproceedings{chawla2023image,
	author={H. {Chawla} and K. {Jeeveswaran} and E. {Arani} and B. {Zonooz}},
	booktitle={2023 IEEE International Conference on Robotics and Automation (ICRA)},
	title={Image Masking for Robust Self-Supervised Monocular Depth Estimation},
	location={London, UK},
	publisher={IEEE},
	year={2023}
}
</pre>

## License

This project is licensed under the terms of the MIT license.
