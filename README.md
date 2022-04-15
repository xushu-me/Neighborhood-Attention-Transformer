# Neighborhood Attention Transformer


Preprint Link: [Neighborhood Attention Transformer
](https://arxiv.org/abs/2204.07143)

By [Ali Hassani<sup>[1, 2]</sup>](https://alihassanijr.com/),
[Steven Walton<sup>[1, 2]</sup>](https://stevenwalton.github.io/),
[Jiachen Li<sup>[1,2]</sup>](https://chrisjuniorli.github.io/), 
[Shen Li<sup>[3]</sup>](https://mrshenli.github.io/), 
and
[Humphrey Shi<sup>[1,2]</sup>](https://www.humphreyshi.com/)

In association with SHI Lab @ University of Oregon & UIUC<sup>[1]</sup> and
Picsart AI Research (PAIR)<sup>[2]</sup>, and Meta/Facebook AI<sup>[3]</sup>


![NAT-Intro](image_assets/intro_dark.png#gh-dark-mode-only)
![NAT-Intro](image_assets/intro_light.png#gh-light-mode-only)


# Abstract
![NAT-Arch](image_assets/model_dark.png#gh-dark-mode-only)
![NAT-Arch](image_assets/model_light.png#gh-light-mode-only)
We present Neighborhood Attention Transformer (NAT), an efficient, 
accurate and scalable hierarchical transformer that works well on 
both image classification and downstream vision tasks. 
It is built upon Neighborhood Attention (NA), 
a simple and flexible attention mechanism that localizes the 
receptive field for each query to its nearest neighboring pixels. 
NA is a localization of self-attention, and approaches it as the 
receptive field size increases. 
It is also equivalent in FLOPs and memory usage to Swin 
Transformer's shifted window attention given the same receptive 
field size, while being less constrained. Furthermore, 
NA includes local inductive biases, which eliminate the need for 
extra operations such as pixel shifts. 
Experimental results on NAT are competitive; 
NAT-Tiny reaches 83.2% top-1 accuracy on ImageNet with only 
4.3 GFLOPs and 28M parameters, 
51.4% mAP on MS-COCO and 48.4% mIoU on ADE20k.


![computeplot_dark](image_assets/computeplot_dark.png#gh-dark-mode-only)
![computeplot_light](image_assets/computeplot_light.png#gh-light-mode-only)

# How it works
Natural Attention localizes the query's (red) receptive field to its nearest neighborhood (green). 
This is equivalent to dot-product self attention when the neighborhood size is identical to the image dimensions. 
Note that the edges are special (edge) cases.

![720p_fast_dm](image_assets/720p_fast_dm.gif#gh-dark-mode-only)
![720p_fast_lm](image_assets/720p_fast_lm.gif#gh-light-mode-only)

# Results and checkpoints
We will release checkpoints for each model along with our code in the coming days.

## Classification
| Model | # of Params | FLOPs | Top-1 |
|---|---|---|---|
| NAT-Mini | 20M | 2.7G | 81.8% |
| NAT-Tiny | 28M | 4.3G | 83.2% |
| NAT-Small | 51M | 7.8G | 83.7% |
| NAT-Base | 90M | 13.7G | 84.3% |

## Object Detection
| Backbone | Network | # of Params | FLOPs | mAP | Mask mAP |
|---|---|---|---|---|---|
| NAT-Mini | Mask R-CNN | 40M | 225G | 46.5 | 41.7 |
| NAT-Tiny | Mask R-CNN | 48M | 258G | 47.7 | 42.6 |
| NAT-Small | Mask R-CNN | 70M | 330G | 48.4 | 43.2 |
| NAT-Mini | Cascade Mask R-CNN | 77M | 704G | 50.3 | 43.6 |
| NAT-Tiny | Cascade Mask R-CNN | 85M | 737G | 51.4 | 44.5 |
| NAT-Small | Cascade Mask R-CNN | 108M | 809G | 52.0 | 44.9 |
| NAT-Base | Cascade Mask R-CNN | 147M | 931G | 52.3 | 45.1 |

## Semantic Segmentation
| Backbone | Network | # of Params | FLOPs | mIoU | mIoU (multi-scale) |
|---|---|---|---|---|---|
| NAT-Mini | Cascade Mask R-CNN | 50M | 900G | 45.1 | 46.4 |
| NAT-Tiny | Cascade Mask R-CNN | 58M | 934G | 47.1 | 48.4 |
| NAT-Small | Cascade Mask R-CNN | 82M | 1010G | 48.0 | 49.5 |
| NAT-Base | Cascade Mask R-CNN | 123M | 1137G | 48.5 | 49.7 |

# Salient maps

| Original | ViT | Swin | NAT |
|---|---|---|---|
| ![img0](image_assets/salient/img0.png) | ![img0-vit-dark](image_assets/salient/img0_vit_dark.png#gh-dark-mode-only)![img0-vit-light](image_assets/salient/img0_vit_light.png#gh-light-mode-only)  | ![img0-swin-dark](image_assets/salient/img0_swin_dark.png#gh-dark-mode-only)![img0-swin-light](image_assets/salient/img0_swin_light.png#gh-light-mode-only) | ![img0-nat-dark](image_assets/salient/img0_nat_dark.png#gh-dark-mode-only)![img0-nat-light](image_assets/salient/img0_nat_light.png#gh-light-mode-only) |
| ![img1](image_assets/salient/img1.png) | ![img1-vit-dark](image_assets/salient/img1_vit_dark.png#gh-dark-mode-only)![img1-vit-light](image_assets/salient/img1_vit_light.png#gh-light-mode-only)  | ![img1-swin-dark](image_assets/salient/img1_swin_dark.png#gh-dark-mode-only)![img1-swin-light](image_assets/salient/img1_swin_light.png#gh-light-mode-only) | ![img1-nat-dark](image_assets/salient/img1_nat_dark.png#gh-dark-mode-only)![img1-nat-light](image_assets/salient/img1_nat_light.png#gh-light-mode-only) |
| ![img2](image_assets/salient/img2.png) | ![img2-vit-dark](image_assets/salient/img2_vit_dark.png#gh-dark-mode-only)![img2-vit-light](image_assets/salient/img2_vit_light.png#gh-light-mode-only)  | ![img2-swin-dark](image_assets/salient/img2_swin_dark.png#gh-dark-mode-only)![img2-swin-light](image_assets/salient/img2_swin_light.png#gh-light-mode-only) | ![img2-nat-dark](image_assets/salient/img2_nat_dark.png#gh-dark-mode-only)![img2-nat-light](image_assets/salient/img2_nat_light.png#gh-light-mode-only) |
| ![img3](image_assets/salient/img3.png) | ![img3-vit-dark](image_assets/salient/img3_vit_dark.png#gh-dark-mode-only)![img3-vit-light](image_assets/salient/img3_vit_light.png#gh-light-mode-only)  | ![img3-swin-dark](image_assets/salient/img3_swin_dark.png#gh-dark-mode-only)![img3-swin-light](image_assets/salient/img3_swin_light.png#gh-light-mode-only) | ![img3-nat-dark](image_assets/salient/img3_nat_dark.png#gh-dark-mode-only)![img3-nat-light](image_assets/salient/img3_nat_light.png#gh-light-mode-only) |


# Citation
```bibtex
@article{hassani2022neighborhood,
	title        = {Neighborhood Attention Transformer},
	author       = {Ali Hassani and Steven Walton and Jiachen Li and Shen Li and Humphrey Shi},
	year         = 2022,
	url          = {https://arxiv.org/abs/2204.07143},
	eprint       = {2204.07143},
	archiveprefix = {arXiv},
	primaryclass = {cs.CV}
}
```
