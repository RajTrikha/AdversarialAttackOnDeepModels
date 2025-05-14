# Jailbreaking Deep Models: Adversarial Attacks on ResNet-34 and DenseNet-121

**Team Members:** 
Raj Trikha, Solomon Martin, Gokuleshwaran

This repository contains our final project for **Deep Learning (CS 6953)** at **New York University (NYU)**. We explore the brittleness of modern image classifiers by mounting a series of white-box and patch‐based adversarial attacks on a pre-trained ResNet-34, and examining how well these attacks transfer to other architectures (e.g. DenseNet-121).

---

## 📝 Project Description

Deep convolutional networks achieve impressive performance on large-scale vision tasks, but they remain vulnerable to small, targeted perturbations. In this project we:

1. **Task 1 (Baseline):** Evaluate ResNet-34 on a 500-image subset of ImageNet (100 classes × 5 samples).  
2. **Task 2 (FGSM):** Implement a single‐step L∞ attack (ε=0.02) via Fast Gradient Sign Method.  
3. **Task 3 (PGD):** Strengthen to a multi‐step Projected Gradient Descent attack (ε=0.02, 10 steps).  
4. **Task 4 (Patch-PGD):** Restrict perturbations to a random 32×32 patch, increase ε to 0.3, and apply PGD.  
5. **Task 5 (Transferability):** Measure Top-1/Top-5 accuracy of all four datasets on DenseNet-121.

Our goal is to drive ResNet-34’s Top-1 accuracy down by ≥70%, and to demonstrate that these perturbations transfer across different model families.

---

## 📊 Project Achievements

- **Clean ResNet-34** on 500-image subset:  
  - Top-1: **76.0%**, Top-5: **94.2%**

- **Adv Set 1 (FGSM, ε=0.02):**  
  - Top-1: **3.6%**, Top-5: **22.0%**  
  - ∼95% relative Top-1 drop

- **Adv Set 2 (PGD, ε=0.02, 10 steps):**  
  - Top-1: **0.0%**, Top-5: **2.2%**  
  - Complete collapse of classification

- **Adv Set 3 (Patch-PGD, ε=0.3, 32×32 patch):**  
  - Top-1: **35.60%**, Top-5: **73.20%** (example)  

- **Transfer to DenseNet-121:**  
  | Dataset                 | Top-1 (%) | Top-5 (%) |
  |:------------------------|----------:|----------:|
  | Clean                   |      74.8 |      93.6 |
  | Adv Set 1 (FGSM)        |      45.8 |      76.2 |
  | Adv Set 2 (PGD)         |      47.4 |      81.6 |
  | Adv Set 3 (Patch-PGD)   |      70.8 |      92.4 |

---

## 🗃️ Data

We use a **500-image** test set drawn from ImageNet-1K:

- **Classes:** 100 random synsets (labels_list.json)  
- **Samples per class:** 5  
- **Raw images:** stored under `TestDataSet/<wnid>/*.JPEG`  
- **Preprocessing:**  
  - Resize to 224×224  
  - Tensor conversion & Normalize(mean=[0.485,0.456,0.406], std=[0.229,0.224,0.225])

---

## 📁 Project Structure

