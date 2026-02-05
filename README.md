# Robust Machine Learning Against Poisoning Attacks Using Distributed Ensemble Learning with Pruning

**Author:** Antonio Mena  
**Department:** Department of Electrical and Computer Engineering  
**Institution:** Rutgers University  
**Contact:** agm139@scarletmail.rutgers.edu

---

## Project Overview

As machine learning systems become integral to security-critical applications—such as spam filtering, autonomous driving, and network intrusion detection—their vulnerability to adversarial threats has emerged as a pressing concern. [cite_start]This project addresses the urgent need for lightweight, scalable defenses against **data poisoning attacks**, where adversaries manipulate training data to corrupt model integrity[cite: 7, 8].

This research investigates **Distributed Ensemble Learning combined with Model Pruning**. We demonstrate that aggregating predictions from multiple models and strategically removing compromised learners effectively mitigates poisoning effects, restoring model performance even after significant degradation.

## Methodology

### 1. Attack Simulation (Label Flipping)
To simulate realistic poisoning scenarios, we conducted experiments using a label-flipping attack:
* [cite_start]**Technique:** Randomly flipping the labels of **3% of training samples** uniformly across classes[cite: 13, 124].
* [cite_start]**Objective:** To mimic an adversary's attempt to degrade model accuracy without triggering outlier detection mechanisms[cite: 13].
* [cite_start]**Rationale:** The poisoning rate balances attack potency and stealth, reflecting real-world constraints faced by malicious actors[cite: 14].

### 2. Distributed Ensemble Architecture
* [cite_start]**Model Composition:** An ensemble of **10 convolutional neural networks (CNNs)** with identical architectures[cite: 15].
* [cite_start]**Training:** Models are trained independently on poisoned data to ensure diversity in learned features[cite: 15].
* [cite_start]**Aggregation:** Predictions are aggregated via **majority voting**[cite: 16].

### 3. Pruning Strategy
* [cite_start]**Mechanism:** The least accurate model is iteratively pruned based on validation performance[cite: 16].
* [cite_start]**Hypothesis:** This approach tests if poisoned models exhibit measurable performance degradation, enabling their identification and removal[cite: 17].

## Experimental Results

We evaluated the defense on MNIST and CIFAR-10 datasets. The results demonstrate that the pruning strategy was highly effective in recovering model accuracy for both datasets, countering the severe performance drops caused by the poisoning attack.

### MNIST Performance
* **Clean Data Accuracy:** 98.1%
* **Poisoned (No Defense):** 16.1%
* **Poisoned (With Pruning):** 85.9%
* **Analysis:** The poisoning attack reduced the ensemble accuracy to near-random levels (16.1%). However, the pruning defense successfully recovered the accuracy to **85.9%**, demonstrating significant robustness.

### CIFAR-10 Performance
* **Clean Data Accuracy:** 96.5%
* **Poisoned (No Defense):** 12.1%
* **Poisoned (With Pruning):** 92.4%
* **Analysis:** Similar to MNIST, the attack devastated the non-pruned ensemble (12.1% accuracy). The pruning defense proved exceptionally effective here, restoring accuracy to **92.4%**, which is comparable to the clean baseline.

## Environment and Constraints

This project prioritizes accessibility and computational efficiency:
* [cite_start]**Platform:** Google Colab CPU environment[cite: 178].
* [cite_start]**Framework:** PyTorch 1.9.0[cite: 178].
* [cite_start]**Hardware:** Experiments were conducted without GPU acceleration to demonstrate viability for resource-limited scenarios[cite: 179].

## Installation and Usage

### Prerequisites
* Python 3.x
* PyTorch 1.9.0
* NumPy

### Setup
1.  Clone the repository:
    ```bash
    git clone [https://github.com/yourusername/robust-ml-poisoning.git](https://github.com/yourusername/robust-ml-poisoning.git)
    ```
2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## Citation

If you reference this work, please cite the associated technical paper:
> [cite_start]A. Mena, "Robust Machine Learning Against Poisoning Attacks Using Distributed Ensemble Learning with Pruning," Rutgers University [cite: 3-5].

---
[cite_start]*This research was conducted as part of coursework for a Security Engineering class[cite: 275].*
