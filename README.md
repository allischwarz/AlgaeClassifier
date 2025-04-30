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

### Model Descriptions

There are multiple trained models you can call via the AlgaeClassifier.ipynb script.

- algaeclassifier_cnn: Custom-built CNN trained, validated, and tested on the entire algae dataset (all 853 images).
- YOLO
- MASK RCN
- SSD
- 
[fill out]



### Abstract

Harmful algae can produce toxic effects on people, fish, shellfish, marine mammals, and birds. Detecting, identifying, and counting algae in water samples under a microscope is difficult, tedious, and time consuming and requires experience and expert knowledge–causing a bottleneck in algae research. An automatic deep learning algae classification model would significantly improve algae detection methods. In this project, I explored the ability to use pre-trained object detection models for algae identification. Three pre-trained models (YOLO, Mask R-CNN, and SSD) were assessed for their ability to identify harmful algae cells in microscopic images after zero-shot, single-shot, and multi-shot learning. In addition, a custom convolutional neural network (CNN) was built and trained on labeled microscopic images of algae. The classification performance of the four models was quantified and compared to determine the best method for creating a robust and highly accurate algae classification model using minimal training data and to determine if transfer learning from the pre-trained models onto algae data was feasible. The ground truth data used to train, validate, and test these models consisted of 853 images spanning 25 algae classes. Overall, results showed that the CNN performed best for classifying algae. The CNN outperformed all three pre-trained models, suggesting that pre-trained models cannot transfer their learning enough after training on up to 20 examples to achieve high performance. The CNN was able to achieve 100% accuracy, precision, and recall with three
convolutional layers, 3x3 kernels, 30 epochs, and a batch size of 64. The pre-trained models performed best when trained on 20 samples. Though the pre-trained models performed well after training on 20 samples in terms of accuracy, their precision and recall were low. Mask R-CNN had the highest accuracy of the pre-trained models (95.11%), followed by YOLO (94.77%), and SSD (91.12%). In conclusion, pre-trained models were not able to transfer their learning to algae classification with high enough performance after training on 20 examples. A custom CNN is the ideal model for algae classification.

### Introduction

Harmful algae can produce toxic effects on people, fish, shellfish, marine mammals, and birds [1]. Global research initiatives aim to detect harmful algae blooms and assess the effects of such harmful algae on the environment and ecosystem. One of the main methods with which this is accomplished is via collecting water samples and viewing them under a microscope to identify and count any harmful algae that may be present. However, this method is tedious, time-consuming, and requires a highly trained individual to detect and label the algae cells. One of the major bottlenecks when analyzing algae in water samples is counting and labeling the algae. Water samples can contain hundreds or thousands of algal cells, many of which look alike and are hard to classify without extensive knowledge and experience. Current practices involve taking pictures of each algal cell with a microscope for each water sample (tens to thousands of samples can be collected per project), labeling each algae image, and then counting how many algae were found in the samples. In addition, algae cells can be difficult to classify because one type of algae can look very different depending on the angle it is viewed at (Figure 1) and some species look very similar (Figure 2). In addition, there are hundreds of algae types, and it can be time consuming to research images of each type of algae and confirm its label.

<img width="1044" alt="Screenshot 2025-04-30 at 9 54 33 AM" src="https://github.com/user-attachments/assets/f097c857-baf8-46af-8af1-0ef11cedb7a9" />


Figure 1. Example of one algae species that can look very different.

### Algae Data

A total of 853 images belonging to the following 25 classes were used to train, validate, and test the models:

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

The cleaned and labeled data were divided into training (70%), validation (15%), and testing (15%) datasets.

## CNN Hyperparameter Tuning

A custom CNN was built, trained, and tuned on microscopic images of algae. Various CNN architectures were assessed and the model hyperparameters were tuned specifically to classify algae. Various hyperparameters were assessed for the CNN, including kernel size, number of convolutional layers, number of epochs, and batch size. Overall, 16 different architectures were assessed (Table 1). The custom-built CNNs were trained on the entire training dataset and validated on the validation dataset. The model was then fed algae images from the testing dataset, and its ability to correctly label the algae were assessed.

Table 1. CNN Hyperparameter Tuning
| CNN Name  | Kernel Size | Layers | Epochs | Batch Size |  
| --------- | ----------- |------- |------- |----------- |
|    CNN1   |     3x3     |   3    |   30   |     32     |
|    CNN2   |     3x3     |   3    |   30   |     64     |
|    CNN3   |     3x3     |   3    |   50   |     32     |
|    CNN4   |     3x3     |   3    |   50   |     64     |
|    CNN5   |     3x3     |   5    |   30   |     32     |
|    CNN6   |     3x3     |   5    |   30   |     64     |
|    CNN7   |     3x3     |   5    |   50   |     32     |
|    CNN8   |     3x3     |   5    |   50   |     64     |
|    CNN9   |     5x5     |   3    |   30   |     32     |
|    CNN10  |     5x5     |   3    |   30   |     64     |
|    CNN11  |     5x5     |   3    |   50   |     32     |
|    CNN12  |     5x5     |   3    |   50   |     64     |
|    CNN13  |     5x5     |   5    |   30   |     32     |
|    CNN14  |     5x5     |   5    |   30   |     64     |
|    CNN15  |     5x5     |   5    |   50   |     32     |
|    CNN16  |     5x5     |   5    |   50   |     64     |


## Pre-Trained Model Training

Since collecting and labeling images of algae for training and developing such a model would be a time-consuming and potentially costly task, the remaining assessed models were pre-trained models. Pre-trained detection/classification models are trained on thousands or millions of images spanning many classes. In theory, their learning could be transferred to images of algae with minor training on algae images labeled with new classes (i.e., species of algae). The pre-trained models included YOLO [1], Mask R-CNN [2], and SSD [3]. The pre-trained models (YOLO, Mask R-CNN, SSD) were assessed for their ability to classify algae after zero-, single-, and multi-shot learning. During zeroshot learning, the models were not given any additional training. During single-shot learning, the models were trained on one image of each class of algae from the training dataset. During multi-shot learning, the models were trained on five, 10, and 20 images of each class of algae from the training dataset. The pre-trained models were then evaluated for their ability to classify algae with the testing dataset.

## Evaluation Metrics

All four models were evaluated for their classification accuracy with the following metrics:
- Accuracy = TP + TNTP + TN + FP + FN
- Precision = TPTP + FP
- Recall = TPTP + FN
where TP: true positive; TN: true negative; FP: false positive; FN: false negative.

### Evaluation 

## CNN Results
The CNN model was assessed with various hyperparameters, as previously outlined in Table 1. Overall, CNN2, CNN4, and CNN10 were the best performing models with accuracies, precisions, and recalls of 100%. Results from all 16 CNNs are outlined in Table 2. Of the top performing models, CNN2 was the fastest and least computationally expensive and was therefore selected as the best CNN architecture for algae classification in this project (algaeclassifier_cnn). The training/validation loss and training/validation accuracy of CNN2 can be seen in Figures 4 and 5, respectively. Figure 4 suggests that the model did not overfit since validation loss continues to decline. 

Figure 4. Training (loss) and validation (val_loss) loss of the CNN2 model. 

Figure 5. Training (accuracy) and validation (val_accuracy) accuracy of the CNN2 model.

### Sources

[2] https://arxiv.org/pdf/1506.02640.pdf
[3] https://arxiv.org/pdf/1703.06870.pdf
[4] https://arxiv.org/pdf/1512.02325.pdf
[5] https://github.com/ultralytics/yolov5


