Bayesian Deep Learning for Lung cancer Classification

A robust deep learning framework for classifying lung cancer from chest CT scans using Bayesian neural networks with uncertainty quantification, specifically designed for extremely imbalanced medical dataset.

🏥 Overview
This project implements a Bayesian deep learning system for lung cancer classification from chest CT scans, addressing the critical need for uncertainty quantification in medical AI. The system provides both diagnostic predictions and clinically-relevant confidence measures essential for radiologist trust and patient safety.

📋 Features
Core Capabilities

Bayesian Uncertainty Quantification: Distinguishes between epistemic (model) and aleatoric (data) uncertainty
Extreme Imbalance Handling: Specialized techniques for rare lung pathologies
Progressive Curriculum Learning: Staged training from balanced to realistic clinical distributions
Ensemble Architecture: Multiple complementary models for robust predictions

Medical AI Innovations

Stable Variational Bayesian Neural Networks: Overcomes training instabilities in medical imaging
Medical-Specific Augmentation: Tailored for chest CT scan characteristics
Clinical Uncertainty Measures: Essential for medical decision support

🗂️ Dataset

Total Images: 1,000 chest CT scans
Classes: 4 lung pathologies

Adenocarcinoma (218 samples)
Squamous cell carcinoma (170 samples)
Normal tissue (215 samples)
Large cell carcinoma (136 samples)


Challenge: Severe class imbalance typical in medical datasets

🔬 Methodology
1. Extreme Imbalance Mitigation

MEGA-SMOTE: Multi-stage synthetic oversampling
Adaptive SMOTE: Class-size aware sampling
Power-scaled class weights: Up to 2.34x for minority classes

2. Progressive Training Strategy

Stage 1: Fully balanced training (150 samples/class)
Stage 2: Gradual imbalance introduction
Stage 3: Full clinical distribution

3. Bayesian Architecture

Stable Variational Dense layers: Carefully calibrated KL divergence
Monte Carlo dropout: Additional uncertainty estimation
Gradual Bayesian activation: Prevents training collapse

4. Model Ensemble

Model 1: DenseNet121 + MEGA-SMOTE
Model 2: ResNet50V2 + Adaptive SMOTE
Model 3: Bayesian DenseNet + Ultra-severe sampling

📊 Results

## Key Results

### Model Performance Summary

| Model | Accuracy | Weighted F1 | AUC | Best Validation Score |
|-------|----------|-------------|-----|-----------------------|
| DenseNet121 + MEGA-SMOTE | 92.86% | 0.9288 | 0.9898 | 92.86% (val) |
| ResNet50V2 + Adaptive-SMOTE | 94.64% | 0.9466 | 0.9926 | 94.64% (val) |
| Bayesian DenseNet121 | 90.18% | 0.9018 | 0.9673 | 90.18% (val) |
| **Ensemble** | **93.24%** | **0.9324** | **0.9915** | - |


### Training Highlights

- Achieved >90% accuracy on all models despite severe class imbalance
- Bayesian model showed excellent calibration with 90.18% accuracy
- ResNet50V2 with Adaptive-SMOTE performed best (94.64% accuracy)
- Ensemble approach combined strengths of all models

## Features

- **Handles Extreme Class Imbalance** with:
  - MEGA-SMOTE and Adaptive-SMOTE sampling
  - Power-scaled class weights (up to 2.34x for minority classes)
  - Progressive training strategy (balanced → gradual → full)

- **STABLE Bayesian Neural Network** with:
  - Proper KL divergence handling
  - Gradual KL weight scheduling
  - Uncertainty quantification (epistemic + aleatoric)

- **Enhanced Model Architectures**:
  - DenseNet121 and ResNet50V2 backbones
  - Attention mechanisms
  - Robust regularization (l1_l2, dropout 0.5)

- **Comprehensive Evaluation**:
  - Test-time augmentation (8 augmentations per image)
  - Ensemble predictions with weighted averaging
  - Detailed performance visualization

## Dataset

The project uses the [Chest CT-Scan Images Dataset](https://www.kaggle.com/datasets/mohamedhanyyy/chest-ctscan-images) from Kaggle, containing CT-scan images of lung conditions.

**Final Class Distribution:**
- Train: 472 samples ([87, 109, 137, 139] per class)
- Val: 119 samples ([22, 27, 35, 35] per class)
- Test: 148 samples ([27, 34, 43, 44] per class)

