# Neural Network Optimization for Resource-Constrained Devices

This project is part of the **MCML 24-25 Lab 2** at the National Technical University of Athens, focusing on **optimizing neural networks for deployment on 8-bit microcontrollers**. The goal is to solve an **intrusion detection problem in IoT environments**, addressing challenges such as limited computational and storage resources, and class imbalance in datasets.

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Microcontroller](#microcontroller)
- [Implementation Steps](#implementation-steps)
- [Results](#results)
- [How to Use](#how-to-use)
- [License](#license)

## Introduction

The project involves deploying a neural network on an **STM32F091RC** microcontroller with the following constraints:
- 8-bit quantization of models
- Limited **128 KB Flash Memory** and **32 KB SRAM**

The task is to optimize a model for **intrusion detection** in an IoT network, achieving high classification performance while adhering to hardware limitations.

## Dataset

The dataset used is a subset of **CICIoT2023**, a widely recognized dataset for intrusion detection. Features:
- **46 features** extracted from network flows
- **940K samples** across **8 classes**:
  - DDoS, DoS, Mirai, Benign, Spoofing, Reconnaissance, Web, BruteForce

For more details, visit the [CICIoT2023 dataset page](https://www.unb.ca/cic/datasets/iotdataset-2023.html).

## Microcontroller

The deployment target is the **STM32F091RC** from STMicroelectronics:
- Core: ARM Cortex-M0
- Flash Memory: 128 KB
- SRAM: 32 KB
- No hardware for floating-point calculations

For more details, see the [STM32F091RC documentation](https://www.st.com/en/microcontrollers-microprocessors/stm32f091rc.html).

## Implementation Steps

### 1. Preprocessing
- Train-validation split
- Feature normalization (e.g., z-score)
- Optional: Data augmentation to address class imbalance

### 2. Model Development
- Built a sequential neural network using TensorFlow
- Optimized layers for compatibility with quantization
- Initial architecture: **20 hidden layers, 64 neurons/layer**, achieving ~93% accuracy and 87% F1-score

### 3. Model Optimization
- Applied quantization-aware training
- Reduced model size to under **10,000 parameters** for deployment

### 4. Evaluation
- Metrics: Accuracy, F1-score, Model size
- Participated in a Kaggle competition for benchmark evaluation:
  [Kaggle Competition Link](https://www.kaggle.com/competitions/mcml-24-25-lab-2-intrusion-detection-in-iot)

## Results

The final model achieved:
- **Accuracy:** ≥90%
- **F1-Score:** Optimized to maintain balance
- **Model Size:** Suitable for the resource constraints of the STM32F091RC
