# DLC + SimBA

## Purpose
* Pose estimation with [**DeepLabCut (DLC)**](https://deeplabcut.github.io/DeepLabCut/README.html)
* Behavior labeling with [**Mouse Action Recognition System (MARS) and BENTO**](https://github.com/neuroethology/MARS)
* Behavioral classification with [**Simple Behavioral Analysis (SimBA)**](https://simba-uw-tf-dev.readthedocs.io/en/latest/index.html) 

## Workflow overview
* **DLC** → extract frames → label body parts in napari → train DLC network → output estimated pose coordinates (.csv/.h5) and videos (.mp4)
* **MARS/BENTO** → manually label frames → output labeled behavioral bouts with start/end time stamps (.annot) 
  * Behaviors: close_investigation, rump_attack, nape_attack, mount, defensive_rear, social_groom, huddle_like
  * Have clear inclusion/exclusion criteria for each behavior
  * Label in an actor-agnostic way
* **SimBA** → create project → import DLC pose estimation (.csv) and MARS behavior labels (.annot) train behavioral classifiers → analyze videos <br/>
  * Follow [this tutorial walkthrough](https://simba-uw-tf-dev.readthedocs.io/en/latest/Scenario1.html) to create a SimBA project
  * [Import MARS annotations](https://github.com/sgoldenlab/simba/blob/master/docs/third_party_annot.md)

## Pre-requisites
1. Install Python 3.x version
2. Install Miniconda3
3. Ideally a GPU with suitable CUDA version and PyTorch installation

### Install DLC
1. Open Anaconda Prompt
2. `conda create --name deeplabcut python=3.12`
3. `conda activate deeplabcut`
4. `pip install torch torchvision --index-url https://download.pytorch.org/whl/cu128` # analysis workstation 1
5. `pip install deeplabcut[gui]`
6. `python -c "import torch; print(torch.cuda.is_available())"` # should print out "True"
7. `python -m deeplabcut` # launch dlc

### Install BENTO
1. Download bento source code zip file from [here](https://github.com/neuroethology/bento/releases)
2. Open Anaconda Prompt
5. `cd path_to_bento_folder`
6. `conda env create -f bento.yml`
7. `python src/bento.py`

### Install SimBA
1. Open Anaconda Prompt
2. `conda create --name simba python=3.6`
3. `conda activate simba`
4. `pip install simba-uw-tf-dev`
5. `simba` # launch simba


## Citations
### DeepLabCut
Mathis A, Mamidanna P, Cury KM, Abe T, Murthy VN, Mathis MW, Bethge M. "DeepLabCut: markerless pose estimation of user-defined body parts with deep learning." Nature Neuroscience 21, 1281–1289 (2018), doi:10.1038/s41593-018-0209-y; and the protocol Nath T, et al. "Using DeepLabCut for 3D markerless pose estimation across species and behaviors." Nature Protocols (2019), doi:10.1038/s41596-019-0176-0.

### SimBA
Goodwin NL, Choong JJ, Hwang S, Pitts K, Bloom L, Islam A, et al. "Simple Behavioral Analysis (SimBA) as a platform for explainable machine learning in behavioral neuroscience." Nature Neuroscience 2024 Jul;27(7):1411–1424, doi:10.1038/s41593-024-01649-9 (senior author Sam A. Golden, University of Washington; PMID 38778146).
