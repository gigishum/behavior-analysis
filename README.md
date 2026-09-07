# DLC + SimBA + custom code

## Purpose
* Pose estimation with [**DeepLabCut (DLC)**](https://deeplabcut.github.io/DeepLabCut/README.html)
* Behavioral classification with [**Simple Behavioral Analysis (SimBA)**](https://simba-uw-tf-dev.readthedocs.io/en/latest/index.html) 
* Downstream behavioral analysis with custom scripts

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

### Install Behavioral Analysis
1. Open Anaconda Prompt
2. `conda create --name behav python=3.13`
3. `conda activate behav`

## Citations
### DeepLabCut
Mathis A, Mamidanna P, Cury KM, Abe T, Murthy VN, Mathis MW, Bethge M. "DeepLabCut: markerless pose estimation of user-defined body parts with deep learning." Nature Neuroscience 21, 1281–1289 (2018), doi:10.1038/s41593-018-0209-y; and the protocol Nath T, et al. "Using DeepLabCut for 3D markerless pose estimation across species and behaviors." Nature Protocols (2019), doi:10.1038/s41596-019-0176-0.

### SimBA
Goodwin NL, Choong JJ, Hwang S, Pitts K, Bloom L, Islam A, et al. "Simple Behavioral Analysis (SimBA) as a platform for explainable machine learning in behavioral neuroscience." Nature Neuroscience 2024 Jul;27(7):1411–1424, doi:10.1038/s41593-024-01649-9 (senior author Sam A. Golden, University of Washington; PMID 38778146).
