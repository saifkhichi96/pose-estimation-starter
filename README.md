# Human Pose Estimation Starter
A PyTorch-based starter kit for 2D human pose estimation projects, designed for researchers working on optimizing human pose estimation networks using knowledge distillation and neural architecture search. It provides an interface for training, inference, and evaluation, as well as the dataloaders for common human pose estimation datasets.

![screenshot](docs/assets/images/screenshot.png)

This repository is a fork of [PyTorch-Pose](https://github.com/bearpaw/pytorch-pose), and also uses code from several other repositories as listed in the [Acknowledgments](#acknowledgments) section.

## Table of Contents
- [Getting Started](#getting-started)
  - [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Structure](#structure)
- [Supported Models](#supported-models)
- [Supported Datasets](#supported-datasets)
- [Contributing](#contributing)
- [Acknowledgments](#acknowledgments)

## Getting Started
These instructions will help you set up the project on your local machine for development and testing purposes.

### Features
- Multi-thread data loading
- Multi-GPU training
- Logger
- Training/testing results visualization

See [Getting Started](docs/getting-started.md) for notes on how to use the project for training and evaluation.

## Prerequisites
- PyTorch 0.4.1 or higher

Note that the original code was developed with Python2 and has not been tested with Python3 yet. If you would like to contribute to the project and update the code to Python3 and a newer version of PyTorch, please feel free to submit a pull request.

## Installation
1. Clone the repository:
```
git clone --recursive https://github.com/saifkhichi96/human-pose-estimation-starter.git
```
2. Install the required Python packages:
```
pip install -r requirements.txt
```
3. Create a symbolic link to the `images` directory of the MPII dataset:
   ```
   ln -s PATH_TO_MPII_IMAGES_DIR data/mpii/images
   ```
   For training/testing on COCO, please refer to [COCO Readme](docs/datasets/coco.md).
4. Download annotation file:
    * (MPII) Download [mpii_annotations.json](https://drive.google.com/open?id=1mQrH_yVHeB93rzCfyq5kC9ZYTwZeMsMm) and save it to `data/mpii`
    * (COCO) Download [coco_annotations_2014.json](https://drive.google.com/open?id=1jrxis4ujrLlkwoD2GOdv3PGzygpQ04k7) or/and [coco_annotations_2017.json](https://drive.google.com/open?id=1YuzpScAfzemwZqUuZBrbBZdoplXEqUse) and save it to `data/coco`

## Usage
1. Download and prepare the dataset following the instructions in the `data/` folder.
2. Train a human pose estimation model by running the training script:
```
python src/train.py --config configs/config.yaml
```
3. Evaluate the model on the test dataset:
```
python src/evaluate.py --config configs/config.yaml
```

## Structure
- `data/`: A folder containing a small dataset for testing purposes and instructions for obtaining larger datasets.
- `notebooks/`: A folder containing Jupyter notebooks to demonstrate the implementation.
- `src/`: A folder containing the main source code for human pose estimation.
- `models/`: A folder with code for various pose estimation models (ViTPose, TokenPose, etc.).
- `utils/`: A folder with utility functions for data loading, preprocessing, and postprocessing.
- `configs/`: A folder containing configuration files for different models and training settings.
- `requirements.txt`: A list of required Python packages.

## Supported Models
The following models are supported:
- [x] Alejandro Newell, Kaiyu Yang, and Jia Deng, Stacked Hourglass Networks for Human Pose Estimation, [arXiv:1603.06937](http://arxiv.org/abs/1603.06937), 2016. ([GitHub](https://github.com/princeton-vl/pose-hg-train))
- [x] Xiao et al., Simple Baselines for Human Pose Estimation and Tracking, [arxiv:1804.06208](https://arxiv.org/abs/1804.06208), ECCV 2018 ([GitHub](https://github.com/Microsoft/human-pose-estimation.pytorch))

For more information on the models, please refer to the [models documentation](docs/models.md).

## Supported Datasets
Dataloaders for the following datasets are provided:
- [x] [COCO](http://cocodataset.org/#keypoints-challenge2017)
- [x] [MPII](http://human-pose.mpi-inf.mpg.de)
- [x] [Leeds Sports Pose (LSP)](http://sam.johnson.io/research/lsp.html)

For more information on the datasets, please refer to the [datasets documentation](docs/datasets.md).

## Roadmap
- [ ] Convert the code to Python3 and PyTorch 2.0
- [ ] Use PyTorch Lightning to reduce boilerplate code
- [ ] Add support for more datasets
  - [ ] [COCO-WholeBody](https://github.com/jin-s13/COCO-WholeBody)
  - [ ] [MPII-TRB](https://github.com/kennymckormick/Triplet-Representation-of-human-Body)
  - [ ] [CrowdPose](https://github.com/Jeff-sjtu/CrowdPose)
  - [ ] [OCHuman](https://github.com/liruilong940607/OCHumanApi)
  - [ ] [Human3.6M](http://vision.imar.ro/human3.6m/description.php)
  - [ ] [MHP](https://lv-mhp.github.io/dataset)
- [ ] Add code to visualize data samples
- [ ] Add support for more models
- [ ] Improve the documentation
  - [ ] Create the models documentation
  - [ ] Create the datasets documentation
  - [ ] Restructure the documentation to make it easier to navigate

## Contributing
Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## Acknowledgments
- [Human-Pose-Estimation-101](https://github.com/cbsudux/Human-Pose-Estimation)
- [PyTorch-Pose](https://github.com/bearpaw/pytorch-pose)
