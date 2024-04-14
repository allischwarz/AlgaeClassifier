# AlgaeClassifier
Classifies microscopic images of algae with 25 classes

### Overview

This repo contains multiple image classification models (see models folder) trained on microscopic images of algae.

### How to Use

The AlgaeClassifier.ipynb script loads and classifies algae images. In the script, change:

- The path of [model_path] to the path to the desired classification model you want to use (see models folder)
- The path of [image_directory] to the path of the folder containing the images you want to classify
- The path of [results_directory] to where you would like the classification results to be saved

Run the script, and it will output classification labels and predictions associated with each image name as well as output an excel file containing this information to the [results_directory] path.

### Algae Data

This code was built using data collected at the Auburn Shellfish Lab on Dauphin Island, AL. A total of 853 images belonging to the following 5 classes were used to train, validate, and test the models:

- Actinoptychus
- Bacillaria
- Biddulphia
- Centric Diatom
- Ciliate
- Coscinodiscus
- Cylindrotheca
- Dactyliosolen
- Diatom
- Dinoflagellate
- Entomoneis
- Euglenoid
- Fragilidium
- Hemiaulus
- Heterosigma Akashiwo
- Lyrella
- Navicula
- Nitzschia
- Odontella
- Paralia
- Pennate Diatom
- Pleurosigma
- Prorocentrum
- Tintinnid
- Tripos Hircus

### Model Descriptions

There are multiple trained models you can call via the AlgaeClassifier.ipynb script.

- algaeclassifier_cnn: Custom-built CNN trained, validated, and tested on the entire algae dataset (all 853).
[fill out]
