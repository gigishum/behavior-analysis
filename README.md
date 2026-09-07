# DLC + SimBA + custom code

## Purpose
* Pose estimation with [**DeepLabCut (DLC)**](https://deeplabcut.github.io/DeepLabCut/README.html)
* Behavioral classification with [**Simple Behavioral Analysis (SimBA)**](https://simba-uw-tf-dev.readthedocs.io/en/latest/index.html) 
* Downstream analysis with **custom code** (quantification, stat tests, generate plots, etc)

## Data structure
* My raw data are resident-intruder assay videos between a C57 (black coat) and BALB/c (white coat), 20-30 minutes, 20 fps, grey scale, 1280 x 1024, around 500-800MB each, stored in NEMO (but when you train DLC, better to have the training dataset videos stored locally on your workstation)
* My folder structure follows the [NeuroBlueprint](https://neuroblueprint.neuroinformatics.dev/latest/index.html) structure, and all my raw videos have metadata.yaml files, which is used in batch running DLC and SimBA, as well as in the custom behavioral analysis scripts
* If you don't have a NeuroBlueprint folder structure, you can still do everything and batch process/analyze, you just need to write a small custom code specifying your video paths so the computer knows 

## Workflow overview

**1. Install DLC and SimBA**
   * You need separate conda environments for DLC and SimBA
   * They are already installed in respective conda environments in Analysis Workstation 1: `deeplabcut` and `simba`

**2. Train DLC + SimBA models**
   * Ideally a workstation with GPU
   * Split your videos into training (70%), validation (15%), and testing (15%)
   * Download your training videos locally to your workstation, this makes I/O much quicker (computer doesn't have to fetch data from cloud every time, it can fetch data locally when training)
   * You can still run both DLC and SimBA relatively quickly on your laptop (even better if you have a Macbook, because DLC supports PyTorch with Apple Silicon chip)
   * For DLC, it takes around 100-200 manually annotated frames to produce a decent model
   * For SimBA, it takes around ??? manually annotated frames to produce a decent model
   * Validate the trained model on your validation videos (NOT your training dataset)
   * Optimize iteratively until you are happy with pose estimation (DLC) and behavior classification (SimBA) results
   * Run your ideal model on your test videos (NOT your training and validation subset)

**3. Run headlessly in batch**
   * Bulk of raw videos in NEMO
   * Run DLC + SimBA on lots of videos headlessly in batch
   * Can couple with HPC
  
**4. Downstream behavioral analysis**
   * Simple: Behavior count, latency, duration, etc
   * Advanced: Markov models, transition probabilities, etc 

## Installation guide

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
