# Sex of the brain
---------------------------------------------------------------------------------------
Predicting brain sex based on EEG data

**Authors:**
- Alexandra Belyaeva [@BelyaevaAlex](https://github.com/BelyaevaAlex), MSU +BI
- Anna Kapitonova [@anna-kapitonova](https://github.com/anna-kapitonova), MSU +BI
- Savelii Komlev [@Unknown-Negotiator](https://github.com/Unknown-Negotiator)
- Anna Ivanova
  
**Scientific supervisor:**

Ilya Zakharov, Brainify.AI
  
## Introduction

For the current project, we proposed to develop ML model that will improve the results of van Putten on the EEG data. Several publicly available datasets exist for that purpose (e.g., TUH dataset, Harati et al., 2015, or TD-Brain dataset, Dijk et al., 2022). We used both handcrafted EEG features and automatically extracted features (e.g., with ML models) for prediction.

##  Our results:

__EEG data preparation and cleaning:__

TDBrain raw data in `.vhdr` format (and data in `.set` format from the second dataset) was processed via MNE library for EEG. Due to experimental conditions there are several sessions for one subjec and we selected only session 1 so that repeated session for one person would not be in analysis. Moreover, experiments with closed and open eyes were separated, too.

Epochs were generated through function `mne.make_fixed_length_epochs` with `duration=4.0` and `overlap=0.5` parameters.
 
__ML model development and validation:__
 
 __DL:__
 
We utilize TorchEEG, a library built on PyTorch for EEG signal analysis. Due to the beta version of the framework, we developed two new custom datasets and implemented built-in deep learning models (convolutional neural networks) based on published papers for EEG analysis. Subsequently, we enhanced these models by adding additional convolutional neural network layers.

Our metric: accuracy 69%

__ML:__

Gradient-boosting on decision trees (extracted features from raw data with https://mne.tools/mne-features/api.html )
