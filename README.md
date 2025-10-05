# 🧬 Automated Malaria Diagnosis using Transfer Learning and CNNs

This repository contains the full source code and analysis notebooks for the **African Leadership University’s Formative Group (7) Assignment** in the **Introduction to Machine Learning** course.

---

## 📖 Project Overview
This project systematically addresses the global health challenge of **malaria diagnosis** by developing and evaluating **five distinct Convolutional Neural Network (CNN) models** for automated classification of **infected vs. uninfected red blood cells** from microscopic images.

We rigorously compare **custom-built architectures** against **state-of-the-art Transfer Learning (TL) models** — *VGG16, ResNet50, and MobileNetV2* — to identify the most **robust, accurate, and efficient solution** suitable for deployment in **resource-constrained settings**.

---

## 📂 Repository Structure

The core analysis is contained within five distinct Jupyter Notebooks, each corresponding to a different model.

| Notebook | Model | Strategy | Primary Focus |
|-----------|--------|-----------|----------------|
| `01_Model_Baseline_CNN.ipynb` | Model 1: Basic CNN | From Scratch | Establishing a performance floor and optimizing a minimal architecture. |
| `02_Model_Advanced_CNN.ipynb` | Model 2: Improved CNN | From Scratch | Demonstrating advanced custom design (BatchNorm, L2, Dropout, GAP). |
| `03_Model_VGG16.ipynb` | Model 3: VGG16 | Transfer Learning (Fine-Tuning) | Evaluating the deep-capacity VGG architecture with partial fine-tuning. |
| `04_Model_ResNet50.ipynb` | Model 4: ResNet50 | Transfer Learning (Feature Extraction) | Testing the robustness of residual connections via initial feature extraction. |
| `05_Model_MobileNetV2.ipynb` | Model 5: MobileNetV2 | Transfer Learning (Feature Extraction) | Optimizing for efficiency and speed using the inverted residual design. |

---

## 🎯 Key Findings & Critical Trade-Offs

### 1️⃣ Overall Comparative Performance
The **Transfer Learning (TL)** models generally outperformed the initial custom designs, confirming the benefit of leveraging pre-trained weights.

| Model | Best Accuracy | Best Recall *(Clinical Priority)* | Design Takeaway |
|--------|----------------|----------------------------------|-----------------|
| **Model 1: Basic CNN** | 0.9577 | 0.9663 | Surprisingly high performance and excellent AUC (0.9884), setting a high benchmark. |
| **Model 3: VGG16** | 0.9620 | 0.9650 | Highest overall accuracy achieved by adapting high-level features through fine-tuning. |
| **Model 5: MobileNetV2** | 0.9292 | 0.9495 | Best Recall among Feature Extraction models, but faced a critical robustness failure. |
| **Model 4: ResNet50** | 0.4900 | 0.4900 | Failed: Complete failure of Feature Extraction due to significant domain shift. |

---

### 2️⃣ The MobileNetV2 Paradox — *Efficiency vs. Robustness*
The **MobileNetV2 experiments (Model 5)** revealed a key limitation of pure Feature Extraction:

- **High Performance:** The best configuration (**E7**) achieved a strong accuracy of **0.9212** and the project’s **highest Recall (0.9495)** among all Feature Extraction models.  
- **Critical Failure:** Despite these scores, every single MobileNetV2 Feature Extraction run (**E1–E7**) yielded an **AUC = 0.50**, meaning no true discriminative power — equivalent to random guessing.  

**Conclusion:** This paradox highlights the necessity of moving from simple Feature Extraction to **Fine-Tuning**, allowing the base network to adapt and resolve the AUC failure.

---

### 3️⃣ Justification for MobileNetV2 Design
MobileNetV2 was chosen for its **architectural efficiency**.  
Its **Depthwise Separable Convolutions** drastically reduce computational cost and parameter count — making it ideal for **low-power, mobile diagnostic devices** in resource-limited healthcare settings.

---

## 🤝 Group Members

| Member | Primary Model |
|---------|----------------|
| **Jallah Sumbo** | Model 3: VGG16 |
| **Theodora Egbunike** | Model 5: MobileNetV2 |
| **Edine Noella Mugisha** | Model 1: Basic CNN |
| **Davy Ngamije** | Model 2: Improved CNN |
| **Patricia Mugabo** | Model 4: ResNet50 |

---

## 🛠️ Required Libraries

To run the notebooks, ensure the following dependencies are installed:

```bash
Python 3.x
TensorFlow / Keras
NumPy
Matplotlib
Scikit-learn
