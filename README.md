# BCCD White Blood Cell Images

## Overview

This project implements a deep learning pipeline for the classification of medical chest X-ray images into four categories:
- eosinophil
- neutrophil
- monocyte
- lymphocyte
- basophil

In total there are 2445 images for training, 525 images for validation and 530 images for testing.
The goal is to create an accurate model capable of distinguishing between these conditions. For the implementation Tensorflow is used.
The data is available on Kaggle: https://www.kaggle.com/datasets/brikwerk/bccd-white-blood-cell

## Project Steps

**Model Setup**

The model is modified for 5-class classification based on an imagenet pretrained **EfficientNetB0** model. Based on that there are four addidional blocks consisting of a Dense layer, a BatchNormalization layer and a dropout layer.

**Training Strategy**

All layers of the base model are frozen to leverage pretrained features. Only the top four blocks are trained on the medical dataset. The total model has 6,066,856 parameters, 2,013,317 of them are trainable. Data augmentation is used to avoid overfitting, to have more various images and to generalize the model.


**Evaluation & Visualization**

Classification metrics such as accuracy, precision, recall, F1-score and AUC are computed.
The results are visualized through a confusion matrix, an accuracy_loss plot and a ROC-curve.

| Class              | Precision | Recall | F1-Score | Support |
|:------------------:|:---------:|:------:|:--------:|:-------:|
| **basophil**       |   1.00    |  1.00  |   1.00   |   106   |
| **eosinophil**     |   0.97    |  0.68  |   0.80   |   106   |
| **lymphocyte**     |   0.99    |  0.99  |   0.99   |   106   |
| **monocyte**       |   0.96    |  0.99  |   0.98   |   106   |
| **neutrophil**     |   0.76    |  0.96  |   0.85   |   106   |
| **accuracy**       |           |        |   0.92   |   530   |
| **macro avg**      |   0.94    |  0.92  |   0.92   |   530   |
| **weighted avg**   |   0.94    |  0.92  |   0.92   |   530   |
