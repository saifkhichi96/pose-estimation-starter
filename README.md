# Human Pose Estimation Starter
A PyTorch-based starter kit for 2D human pose estimation projects, designed for students working on optimizing human pose estimation networks using knowledge distillation and neural architecture search.

This repository is a fork of [PyTorch-Pose](https://github.com/bearpaw/pytorch-pose), which provides a PyTorch implementation of the general pipeline for 2D single human pose estimation. The aim is to provide the interface of the training/inference/evaluation, and the dataloader with various data augmentation options for the most popular human pose databases (e.g., [the MPII human pose](http://human-pose.mpi-inf.mpg.de), [LSP](http://www.comp.leeds.ac.uk/mat4saj/lsp.html) and [FLIC](http://bensapp.github.io/flic-dataset.html)).

![screenshot](./docs/screenshot.png)

Additionally, it includes the content from [Human-Pose-Estimation-101](https://github.com/cbsudux/Human-Pose-Estimation-101) to help understand the basics of human pose estimation. Some codes for data preparation and augmentation are brought from the [Stacked hourglass network](https://github.com/anewell/pose-hg-train). Thanks to the original authors.

## Table of Contents
- [Getting Started](#getting-started)
  - [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Structure](#structure)
- [Basics of Human Pose Estimation](#basics-of-human-pose-estimation)
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

See [Getting Started](docs/GETTING_STARTED.md) for notes on how to use the project for training and evaluation.

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
   For training/testing on COCO, please refer to [COCO Readme](data/coco/README.md).
4. Download annotation file:
    * (MPII) Download [mpii_annotations.json](https://drive.google.com/open?id=1mQrH_yVHeB93rzCfyq5kC9ZYTwZeMsMm) and save it to `data/mpii`
    * (MSCOCO) Download [coco_annotations_2014.json](https://drive.google.com/open?id=1jrxis4ujrLlkwoD2GOdv3PGzygpQ04k7) or/and [coco_annotations_2017.json](https://drive.google.com/open?id=1YuzpScAfzemwZqUuZBrbBZdoplXEqUse) and save it to `data/coco`

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

## Basics of Human Pose Estimation
For a more comprehensive understanding of human pose estimation, including 2D and 3D pose estimation basics, loss functions, evaluation metrics, and applications, please refer to the [BASICS.md](BASICS.md) file, which is based on the content from [Human-Pose-Estimation-101](https://github.com/cbsudux/Human-Pose-Estimation-101).

## Supported Models
- [x] [Stacked Hourglass networks](https://arxiv.org/abs/1603.06937)
- [x] Xiao et al., Simple Baselines for Human Pose Estimation and Tracking, ECCV 2018 ([PDF](https://arxiv.org/abs/1804.06208) | [GitHub](https://github.com/Microsoft/human-pose-estimation.pytorch))

## Supported Datasets
- [x] [MPII human pose](http://human-pose.mpi-inf.mpg.de)
- [x] [Leeds Sports Pose (LSP)](http://sam.johnson.io/research/lsp.html)
- [x] [MSCOCO (single person)](http://cocodataset.org/#keypoints-challenge2017)

## Contributing
Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## Acknowledgments
- [Human-Pose-Estimation-101](https://github.com/cbsudux/Human-Pose-Estimation)
- [PyTorch-Pose](https://github.com/bearpaw/pytorch-pose)
