# Behavioral Analysis

## Purpose
* Pose estimation with [**DeepLabCut (DLC)**](https://deeplabcut.github.io/DeepLabCut/README.html)
* Behavior labeling with [**Mouse Action Recognition System (MARS) and BENTO**](https://github.com/neuroethology/MARS)
* Behavioral classification with [**Simple Behavioral Analysis (SimBA)**](https://simba-uw-tf-dev.readthedocs.io/en/latest/index.html) 

## Workflow overview
* **DLC** → extract frames → label body parts in napari → train DLC network → output estimated pose coordinates (.csv/.h5) and videos (.mp4)
  * Follow [this tutorial walkthrough](https://deeplabcut.github.io/DeepLabCut/docs/beginner-guides/beginners-guide.html) to create a DLC project
  * Annotating 100-200 frames from 10 videos would already give you a pretty good result
* **MARS/BENTO** → manually label frames → output labeled behavioral bouts with start/end time stamps (.annot) 
  * Have clear inclusion/exclusion criteria for each behavior
  * Label in an actor-agnostic way
* **SimBA** → create project → import DLC pose estimation (.csv) and MARS behavior labels (.annot) train behavioral classifiers → analyze videos <br/>
  * Follow [this tutorial walkthrough](https://simba-uw-tf-dev.readthedocs.io/en/latest/Scenario1.html) to create a SimBA project
  * SimBA trains a separate random forest classifier for each behavior
  * You can annotate videos using the SimBA GUI, but I do it using Caltech's [MARS/BENTO](https://github.com/neuroethology/bentoMAT)
  * [Import MARS annotations](https://github.com/sgoldenlab/simba/blob/master/docs/third_party_annot.md) to SimBA

## Pre-requisites
1. Install Python 3.x version
2. Install Miniconda3
3. Ideally work on a workstation with GPU

### Install DLC
1. Open Anaconda Prompt
2. `conda create --name deeplabcut python=3.12`
3. `conda activate deeplabcut`
4. `pip install torch torchvision --index-url https://download.pytorch.org/whl/cu128` # analysis workstation 1
5. `pip install deeplabcut[gui]`
6. `python -c "import torch; print(torch.cuda.is_available())"` # should print out "True"
7. `python -m deeplabcut` # launch dlc

### Install BENTO
1. Download the zip file from my forked directory [here](https://github.com/gigishum/bento)
2. Open Anaconda Prompt
5. `cd path_to_bento_folder`
6. `conda env create -f bento.yml`
7. `conda activate bento`
8. `pip install colour-science==0.4.6 --no-deps`
9. `pip install colour-demosaicing==0.2.6 --no-deps`
10. `python src/bento.py` # launch bento

### Install SimBA
1. Open Anaconda Prompt
2. `conda create --name simba python=3.6`
3. `conda activate simba`
4. `pip install simba-uw-tf-dev`
5. `simba` # launch simba


## Citations
**DeepLabCut**\
Mathis, Alexander, et al. "DeepLabCut: markerless pose estimation of user-defined body parts with deep learning." Nature neuroscience 21.9 (2018): 1281-1289.

**MARS/BENTO**\
Segalin, Cristina, et al. "The Mouse Action Recognition System (MARS) software pipeline for automated analysis of social behaviors in mice." Elife 10 (2021): e63720.

**SimBA**\
Goodwin, Nastacia L., et al. "Simple Behavioral Analysis (SimBA) as a platform for explainable machine learning in behavioral neuroscience." Nature neuroscience 27.7 (2024): 1411-1424.
