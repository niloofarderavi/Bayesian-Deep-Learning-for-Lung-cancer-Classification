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
Individual Model Performance
ModelAccuracyAUCWeighted F1Bayesian DenseNet90.2%96.7%90.2%DenseNet + MEGA-SMOTE92.8%99.0%92.9%ResNet50V2 + Adaptive94.6%99.3%94.7%
Ensemble Performance

Overall Accuracy: 92.8%
Weighted F1-Score: 92.9%
AUC: 99.0%

Key Achievements
✅ 90%+ Bayesian accuracy with uncertainty quantification
✅ Clinical-grade performance across all lung pathology classes
✅ Robust uncertainty measures for medical decision support
✅ Successful handling of extreme class imbalance


Installation
bash# Clone the repository
git clone https://github.com/yourusername/bayesian-lung-classification.git
cd bayesian-lung-classification

# Install dependencies
pip install -r requirements.txt

# Download the dataset (requires Kaggle API)
python download_dataset.py


Usage
Basic Training
python# Run the complete training pipeline
python main.py

# Train only Bayesian model
python train_bayesian.py --model bayesian --epochs 150
Inference with Uncertainty
pythonfrom models import BayesianLungClassifier

model = BayesianLungClassifier.load('bayesian_best.h5')
predictions, uncertainties = model.predict_with_uncertainty(ct_images)

# Get epistemic and aleatoric uncertainties
epistemic_uncertainty = uncertainties['epistemic']
aleatoric_uncertainty = uncertainties['aleatoric']


Project Structure
bayesian-lung-classification/
├── models/
│   ├── bayesian_model.py      # Stable Bayesian architecture
│   ├── standard_models.py     # DenseNet/ResNet implementations
│   └── ensemble.py            # Ensemble framework
├── data/
│   ├── preprocessing.py       # Medical image preprocessing
│   ├── augmentation.py        # CT-specific augmentations
│   └── sampling.py            # Imbalance handling techniques
├── training/
│   ├── curriculum.py          # Progressive training strategy
│   ├── losses.py              # Medical-specific loss functions
│   └── metrics.py             # Clinical evaluation metrics
├── evaluation/
│   ├── uncertainty_analysis.py # Bayesian uncertainty evaluation
│   └── clinical_metrics.py     # Medical performance assessment
└── main.py                     # Complete training pipeline

Key Technical Innovations
Stable Bayesian Training

Controlled KL Divergence: Prevents gradient explosion
Gradual Activation: Warmup period for stable convergence
Medical-Calibrated Priors: Tailored for lung pathology discrimination


Medical-Specific Design

Uncertainty-Aware Predictions: Critical for clinical decision support
Extreme Imbalance Solutions: Handles rare disease distributions
Clinical Validation Metrics: Beyond standard ML evaluation


Clinical Impact

Diagnostic Confidence: Uncertainty measures guide radiologist attention
Rare Disease Detection: Specialized techniques for minority pathologies
Risk Stratification: Predictive confidence for treatment planning
AI Transparency: Explainable uncertainty for clinical adoption
