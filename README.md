# Classification using multi modalities of data: Classifying data point class with audio-image pair
Human Identitfication using Multi-Modal models, using audio-image pair, and also seperately.

## Raw Data
VoxCeleb Raw Data was used in this project [VoxCeleb Data](https://www.robots.ox.ac.uk/~vgg/research/CMBiometrics/), which is a large scale audio-visual dataset of human speech. Following are the download links to raw data used:-
* [Image Data](http://www.robots.ox.ac.uk/~vgg/research/CMBiometrics/data/zippedFaces.tar.gz)
* [Audio Data](https://thor.robots.ox.ac.uk/~vgg/data/voxceleb/vox1a/vox1_test_wav.zip)

## Data Selection
Data Selection is done locally using Windows File Manager Only.
* Subset of Image Data is created according to the audio data available, and named as subSetFaces.

## Pre-Processing Data
All Pre-Processing of Data is done in **models.ipynb** only.
1. Getting, Cropping and saving Image Data in np array of np.unit8 format from subSetFaces as 100 images per person for 40 persons, creating labels.
2. Getting and Trimming Audio Data to equal sizes, as 100 audio files per persona for 40 persons.
3. Converting equal sized Audio Files into spectograms with log frequency, and storing it in the form of np array in np.unit8 format.
4. Mapping Images Audio to Audio-Image Paired Data.
5. Both Images and Audio are Rescaled from 0 to 1 inside Models in Rescaling Layer, this is to save memory as storing data in the form of np.unit8 format is much less expensive than storing them in float64 format.

## Models Used
1. CNN for Image Classification:- This model consists of One Preprocessing Rescaling Layer, Two Convolution2D Layers with L2 Regularization, Two MaxPooling2D Layers, One Flatten Layer, Two Dense Layers and One Dropout Layer.
2. CNN for Audio Classification:- This model consists of One Preprocessing Rescaling Layer, Two Convolution2D Layers with L2 Regularization, Two MaxPooling2D Layers, One Flatten Layer, Two Dense Layers.
3. CRNN for Audio Classification:- This model consists of One Preprocessing Rescalingn Layer, Two Convolution1D Layers with L2 Regularization, Two MaxPooling1D Layers, One LSTM Layers, Two Dense Layers.
4. CNN-CNN Parrallel Multi-Modal Model:- This model consists of 1st and 2nd Models in prallel and Fusion Model with Two Dense Layers and One Dropout Layer.
5. CNN-CRNN Parrallel Multi-Modal Model:- This model consists of 1st and 3rd Models in prallel and Fusion Model with Two Dense Layers and One Dropout Layer.

## Requirements
* Python 3
* Matplotlib
* PIL
* numpy
* librosa

## Results
| Model | Training Accuracy | Valiation Accuracy |
| ------ | ---------------- | ------------------ |
| CNN Image Classification | 100.0% | 84.50% |
| CNN Audio Classification | 100.0% | 79% |
| CRNN Audio Classification | 79.75% | 71.50% |
| CNN-CNN Multi Modal Model | 99.86% | 73.25% |
| CNN-CRNN Multi Modal Model | 99.92% | 80.00% |

## How to Run
Run **models.ipynb** file
