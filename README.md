# DLC + SimBA + custom code

## Purpose
* Pose estimation with [**DeepLabCut (DLC)**](https://deeplabcut.github.io/DeepLabCut/README.html)
* Behavioral classification with [**Simple Behavioral Analysis (SimBA)**](https://simba-uw-tf-dev.readthedocs.io/en/latest/index.html) 
* Downstream behavioral analysis with **custom code** (quantification, stat tests, generate plots, etc)

## Workflow overview
DLC project creation → labeling → training → analysis → SimBA import → classification → downstream notebooks

## Installation

### Install DLC
1. Open Anaconda Prompt
2. `conda create --name deeplabcut python=3.12`
3. `conda activate deeplabcut`


### Install SimBA
1. Open Anaconda Prompt
2. `conda create --name simba python=3.6`
3. `conda activate simba`

### Install behavioral analysis dependencies
1. Open Anaconda Prompt
2. `conda create --name behav python=3.13`
3. `conda activate behav`
