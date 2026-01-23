# Alzheimer’s Disease MRI Classification using Deep Learning 

## Project Overview

This project aims to detect and classify different stages of Alzheimer’s disease using brain MRI images and a Convolutional Neural Network (CNN).

The model classifies MRI scans into four classes:

- Non-Demented  
- Very Mild Demented  
- Mild Demented  
- Demented  

---

## Dataset

The dataset used is the **OASIS MRI Dataset**: https://www.kaggle.com/datasets/ninadaithal/imagesoasis/data

### Dataset Description

- Around 80,000 brain MRI images  
- MRI scans from 461 patients  
- 2D slices are used as input to the neural network  
- Each MRI volume was sliced along the z-axis into 256 slices  
- Only slices from 100 to 160 were selected (most informative brain regions)  
- This results in 61 slices per patient and around 80,000 total images  

### Classes Distribution

- Non Demented: ~67,200 images  
- Very Mild Demented: ~13,700 images  
- Mild Demented: ~5,002 images  
- Demented: ~488 images  

The dataset is highly imbalanced, especially for the Demented class.

---

## Handling Data Imbalance

To solve the class imbalance problem, the following techniques were used:

- Oversampling of minority classes  
- Data augmentation  
- Same model architecture and strategy as the reference research paper  

---

## Model Overview

- CNN implemented using TensorFlow / Keras  
- Input size: `128 × 128 × 1` (grayscale MRI slices)  
- Architecture:
  - Three convolution blocks (Conv2D + MaxPooling + BatchNormalization)  
  - Fully connected layer with Dropout and L2 regularization  
  - Softmax output layer with 4 classes  

The model is designed to be simple, efficient, and suitable for medical image classification.

---

## Training and Evaluation

- Optimizer: Adam  
- Loss function: Categorical Crossentropy  
- Callbacks:
  - EarlyStopping  
  - ReduceLROnPlateau  

### Evaluation Strategy

Due to the severe class imbalance in the dataset, this project does not rely only on overall accuracy. Instead, special attention is given to recall for each class, especially the minority classes (Mild Demented and Demented), since in medical diagnosis missing positive cases is more critical than overall accuracy.

### Results

- Training accuracy: ~96%  
- Validation accuracy: ~98%  
- Best model restored from epoch 7
- In addition to high overall accuracy, the use of oversampling and data augmentation significantly improved the recall for each class, especially for the **minority classes**, leading to better detection of Mild Demented and Demented cases.

---

## Reference

[Link to the paper] https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1563016/full
