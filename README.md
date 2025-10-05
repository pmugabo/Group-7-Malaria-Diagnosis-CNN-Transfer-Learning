Automated Malaria Diagnosis using Transfer Learning and CNNs
This repository contains the full source code and analysis notebooks for the African Leadership University's Formative Group (7) Assignment for the Introduction to Machine Learning Program.

Project Overview
This project systematically addresses the global health challenge of malaria diagnosis by developing and evaluating five distinct Convolutional Neural Network (CNN) models for the automated classification of infected and uninfected red blood cells from microscopic images.

We rigorously compare custom-built architectures against state-of-the-art Transfer Learning (TL) models (VGG16, ResNet50, MobileNetV2) to identify the most robust, accurate, and efficient solution suitable for deployment in resource-constrained settings.

💾 Repository Structure
The core analysis is contained within five distinct Jupyter Notebooks, corresponding to the five mandated models.

Notebook	Model	Strategy	Primary Focus
01_Model_Baseline_CNN.ipynb	Model 1: Basic CNN	From Scratch	Establishing a performance floor and optimizing a minimal architecture.
02_Model_Advanced_CNN.ipynb	Model 2: Improved CNN	From Scratch	Demonstrating advanced custom design (BatchNorm, L2, Dropout, GAP).
03_Model_VGG16.ipynb	Model 3: VGG16	Transfer Learning (Fine-Tuning)	Evaluating the deep-capacity VGG architecture with partial fine-tuning.
04_Model_ResNet50.ipynb	Model 4: ResNet50	Transfer Learning (Feature Extraction)	Testing the robustness of residual connections via initial feature extraction.
05_Model_MobileNetV2.ipynb	Model 5: MobileNetV2	Transfer Learning (Feature Extraction)	Optimizing for efficiency and speed using the inverted residual design.

Export to Sheets
🎯 Key Findings & Critical Trade-Offs
1. Overall Comparative Performance
The Transfer Learning (TL) models generally outperformed the initial custom designs, confirming the benefit of leveraging pre-trained weights.

Model	Best Accuracy	Best Recall (Clinical Priority)	Design Takeaway
Model 1: Basic CNN	0.9577	0.9663	Surprisingly high performance and excellent AUC (0.9884), setting a high benchmark for subsequent models.
Model 3: VGG16	0.9620	0.9650	Highest overall accuracy achieved by adapting high-level features through fine-tuning.
Model 5: MobileNetV2	0.9292	0.9495	Best Recall among Feature Extraction models, but faced a critical robustness failure (see below).
Model 4: ResNet50	0.4900	0.4900	Failed: Complete failure of Feature Extraction due to significant domain shift.

Export to Sheets
2. The MobileNetV2 Paradox (Efficiency vs. Robustness)
The MobileNetV2 experiments (Model 5) highlighted a crucial limitation of the Feature Extraction strategy:

High Performance: The best configuration (E7) achieved a strong accuracy of 0.9212 and the project's highest Recall of 0.9495 among all Feature Extraction experiments.

Critical Failure: Despite high Accuracy, every single MobileNetV2 Feature Extraction run (E1-E7) yielded an AUC (Area Under the Curve) of 0.50. An AUC of 0.50 implies the model has no discriminative power and performs no better than random guessing across different decision thresholds.

Conclusion: This paradox justifies the necessity of moving beyond simple Feature Extraction to Fine-Tuning to adapt the base network and resolve the AUC failure.

3. Justification for MobileNetV2 Design
MobileNetV2 was chosen specifically for its architectural efficiency. Its use of Depthwise Separable Convolutions drastically reduces computational cost and parameter count, making it the ideal candidate for a diagnostic solution intended for low-power, mobile devices.

🤝 Group Members
Member	Primary Model
Jallah Sumbo	Model 3: VGG16
Theodora Egbunike	Model 5: MobileNetV2
Edine Noella Mugisha	Model 1: Basic CNN
Davy Ngamije	Model 2: Improved CNN
Patricia Mugabo	Model 4: ResNet50

Export to Sheets
🛠️ Required Libraries
To run the notebooks, ensure you have the following installed:

Python 3.x

TensorFlow / Keras

NumPy

Matplotlib

`Scikit-learn






Tools

Gemini can ma
