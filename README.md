# EA-3DGS:Efficient and Adaptive 3D Gaussians with Highly Enhanced Quality for outdoor scenes

## Overview
![image](https://github.com/user-attachments/assets/53117827-afae-4e42-b8bf-4547c71ef493)

**Abstract**:The mainstream outdoor scene reconstruction methods based on NeRF often exhibit limitations in visual quality and rendering speed. The recently popular 3DGS demonstrates improved performance in small-scale scenes; however, when applied to outdoor environments, the explicit point-based representation described in the original paper lacks effective adjustment methods. Moreover, the presence of hundreds of millions of Gaussian components frequently leads to memory shortages during training, and the model itself incurs significant storage overhead.To address these challenges, we propose EA-3DGS, a high-quality reconstruction method designed for real-time rendering of outdoor scenes based on 3DGS. Our approach introduces a grid system for adjusting Gaussian initialization, subdivides the overall grid through an adaptive representation of tetrahedra, and completes initialization on each grid face, effectively presenting the geometric structure of the grid. During the training process, we optimize the number of Gaussians through Gaussian pruning and spatial perception densification to satisfy the requirements of standard graphics cards, ultimately compressing the entire model via vector quantization.Our method outperforms existing NeRF-based techniques, achieving high fidelity and rapid rendering across multiple outdoor scene datasets.  
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
![image](https://github.com/user-attachments/assets/02bbeb52-6000-40f1-b025-b5ecdd024d19)

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

