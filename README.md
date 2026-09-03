# DLC + SimBA + custom code

## Purpose
* Pose estimation with [**DeepLabCut (DLC)**](https://deeplabcut.github.io/DeepLabCut/README.html)
* Behavioral classification with [**Simple Behavioral Analysis (SimBA)**](https://simba-uw-tf-dev.readthedocs.io/en/latest/index.html) 
* Downstream analysis with **custom code** (quantification, stat tests, generate plots, etc)

## Workflow overview

**1. Raw behavior recordings in NEMO**
   * I organize my NEMO folders in a [NeuroBlueprint](https://neuroblueprint.neuroinformatics.dev/latest/index.html) format 
   * This allows me to use metadata files and automate downstream analysis in batch much quicker and easier

**2. Download a training subset locally**
   * Download a training subset locally to your workstation where you're going to train DLC and SimBA
   * Ideally a workstation with GPU
   * You can still run both DLC and SimBA relatively quickly on your laptop
   * Even better if you have a Macbook, because DLC supports PyTorch with Apple Silicon chip
   
**3. Install DLC and SimBA**
   * You need separate conda environments for DLC and SimBA
   * They are already installed in respective conda environments in Analysis Workstation 1: `deeplabcut` and `simba`

**4. Train DLC + SimBA models**
   * Follow official documentation on how to train:
   * Validate on videos that are not your training dataset
   * Optimize iteratively until you are happy with pose estimation (DLC) and behavior classification (SimBA) results

**5. Run headlessly in batch**
   * Bulk of raw videos in NEMO
   * Run DLC + SimBA on lots of videos headlessly in batch
   * Can couple with HPC
  
**6. Downstream behavioral analysis**
   * Simple: Behavior count, latency, duration, etc
   * Advanced: Markov models, transition probabilities, etc 

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
