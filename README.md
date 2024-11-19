# ECG Signal Anomaly Detection Using CNN Autoencoder

This repository explores the fascinating field of electrocardiogram (ECG) signal processing and classification using a Convolutional Neural Network (CNN) Autoencoder. Leveraging the PTB Diagnostic ECG Database, we aim to detect anomalous ECG signals with high accuracy, utilizing advanced machine learning techniques.

---

## Table of Contents
- [Dataset Overview](#dataset-overview)
- [Project Workflow](#project-workflow)
- [Model Architecture](#model-architecture)
- [Performance Metrics](#performance-metrics)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

---

## Dataset Overview

The project utilizes the **PTB Diagnostic ECG Database** from PhysioNet, comprising 14,552 ECG recordings sampled at 125 Hz. The data is categorized into two classes:

- **Normal heartbeats**  
- **Anomalous heartbeats (associated with cardiac abnormalities)**

**Key Statistics**:
- **Number of Samples**: 14,552  
- **Categories**: Normal, Anomaly  
- **Sampling Frequency**: 125 Hz  

---

## Project Workflow

### 1. Exploratory Data Analysis (EDA):
- Compared patterns of normal and anomalous signals through sample plots.
- Visualized smoothed mean and variability using rolling statistics for both classes.

### 2. Preprocessing:
- Normalized and reshaped data for compatibility with the CNN Autoencoder.
- Split data into training (85%) and testing (15%) sets.

### 3. Model Design:
- Implemented a CNN Autoencoder to detect anomalies based on reconstruction loss.
  - Encoder compresses input signals into latent features.
  - Decoder reconstructs signals from latent representations.

### 4. Evaluation:
- Compared reconstruction loss for normal and anomalous signals.
- Established a threshold based on training data loss distribution.

---

## Model Architecture

### Autoencoder Design

#### Encoder:
- 3 convolutional layers with ReLU activations, batch normalization, and max-pooling.

#### Decoder:
- 3 transposed convolutional layers with ReLU activations and batch normalization.
- Dense layer to reconstruct input dimensions.

#### Improvements:
- Transposed Convolution enhanced reconstruction performance compared to upsampling layers.

**Summary**:  

| Layer Type          | Number of Filters | Kernel Size | Activation |
|---------------------|-------------------|-------------|------------|
| Conv1D + MaxPooling | 128               | 3           | ReLU       |
| Conv1DTranspose     | 128               | 3           | ReLU       |

---

## Performance Metrics

| Metric               | Accuracy | Precision | Recall | F1 Score |
|-----------------------|----------|-----------|--------|----------|
| **With Upsampling**   | 71.99%   | 49.78%    | 87.91% | 63.57%   |
| **With Transposed Conv** | 76.93%   | 55.23%    | 89.81% | 68.40%   |


