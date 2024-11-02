# EA-3DGS:Efficient and Adaptive 3D Gaussians with Highly Enhanced Quality for outdoor scenes

## Overview
![image](https://github.com/user-attachments/assets/53117827-afae-4e42-b8bf-4547c71ef493)

**Abstract**:Efficient scene representations are essential for many real-world applications. Although current NeRF-based methods have achieved impressive results in reconstructing building-scale scenes, they still suffer from slow training and inference speeds due to time-consuming stochastic sampling.
Recently, 3D Gaussian Splatting (3DGS) has demonstrated excellent performance with its high-quality rendering and real-time speed, especially for objects and small-scale scenes. However, in outdoor scenes, its point-based explicit representation lacks an effective adjustment mechanism, and the millions of Gaussian points required often lead to memory constraints during training. To address these challenges, we propose EA-3DGS, a high-quality real-time rendering method designed for outdoor scenes. First, we introduce a mesh structure to regulate the initialization of Gaussian components by leveraging an adaptive tetrahedral mesh that partitions the grid and initializes Gaussian components on each face, effectively capturing geometric structures in low-texture regions. Second, we propose an efficient Gaussian pruning strategy that evaluates each 3D Gaussian's contribution to the view and prunes accordingly. To retain geometry-critical Gaussian points, we also present a structure-aware densification strategy that densifies Gaussian points in low-curvature regions. Additionally, we employ vector quantization for parameter quantization of Gaussian components, significantly reducing disk space requirements with only a minimal impact on rendering quality. Extensive experiments on 13 scenes, including eight from four public datasets (MatrixCity-Aerial, Mill-19, Tanks \& Temples, WHU) and five self-collected scenes from SCUT-CA and plateau regions, further demonstrate the superiority  of our method.
## Dataset
We performe experiments on eight scenes from four public datasets from the Mega-NeRF, MatrixCity, 3D Gaussian Splatting and WHU dataset.

Mill-19 dataset:
Please download the data from the [Mega-NeRF](https://github.com/cmusatyalab/mega-nerf)

MatrixCity-Aerial dataset:
Please download the data from the [MatrixCity](https://city-super.github.io/matrixcity/)

Tanks & Temples dataset:
Please download the data from the [3D Gaussian Splatting](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/)

WHU dataset:
Please download the data from the [WHU dataset](http://gpcv.whu.edu.cn/data/)

We performe experiments on five self-collected scenes(SCUT Campus and plateau regions).

Please concat us:

Jianlin Guo and Haihong Xiao: 202321016915@mail.scut.edu.cn; auhhxiao@mail.scut.edu.cn

Prof. Wenxiong Kang: auwxkang@scut.edu.cn

## Installation

Since, the software is based on original [GaMeS](https://github.com/waczjoan/gaussian-mesh-splatting/tree/main) repository, for details regarding requirements, we kindly direct you to check it.
```shell
# Clone the repo and install dependencies
git clone https://github.com/SCUT-BIP-Lab/EA-3DGS.git
cd EA-3DGS
conda env create --file environment.yml
conda activate ea-3dgs
```
## Training and Evaluation

We use `num_splats` to set number of Gaussian per face. And you can use [Gaussian Opacity Fields](https://github.com/autonomousvision/gaussian-opacity-fields) to get an adaptive tetrahedral mesh to add to your experiment. In order to adapt to large-scale scenarios, the default value of `data_device` is `cpu`. You can adjust it to `cuda` according to the actual situation.
```shell
python train.py --eval -s $DATASET_PATH -m $OUTPUT_PATH --gs_type gs_mesh  -w
python scripts/render.py -m $OUTPUT_PATH --gs_type gs_mesh
python metrics.py -m $OUTPUT_PATH --gs_type gs_mesh
```
## Result
Visual comparisons on Mill-19 and MatrixCity dataset:
![image](https://github.com/user-attachments/assets/ef0d4016-07a4-485e-8a50-2d24ce816d60)
Visual comparisons on WHU dataset and Plateau Region scenes:
![1730015893879](https://github.com/user-attachments/assets/1da2066e-9e3a-4813-9aa3-c766e941eec3)


## Acknowledgements
Our code is derived from many great repositories, appreciate their outstanding work.
- [Mega-NeRF](https://github.com/cmusatyalab/mega-nerf)
- [Switch-NeRF](https://github.com/MiZhenxing/Switch-NeRF)
- [3DGS](https://github.com/graphdeco-inria/gaussian-splatting)
- [GaMeS](https://github.com/waczjoan/gaussian-mesh-splatting)
- [GOF](https://github.com/autonomousvision/gaussian-opacity-fields)
- [Scaffold-GS](https://github.com/city-super/Scaffold-GS/tree/main)
- [Compact-3DGS](https://github.com/maincold2/Compact-3DGS)
- [LightGaussian](https://github.com/VITA-Group/LightGaussian)
- [CompGS](https://github.com/UCDvision/compact3d)

