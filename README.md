# 📊 Examining Bias in LLM Prompt Chaining

This project explores how **prompt chaining** in Large Language Models (LLMs) influences the **propagation of social biases**. Using the [StereoSet dataset](https://huggingface.co/datasets/McGill-NLP/stereoset) and **Meta’s LLaMA 3.1 (8B-Instruct)**, we compare **direct prompting** against **multi-step chained prompting** to quantify how bias evolves across different chain lengths.

Our findings suggest that:
- **2–3 step chains** often reduce bias, especially with explicit stereotype reflection.  
- **4+ step chains** may reintroduce or amplify bias, particularly in **gender** and **profession** categories.  
- Modern instruction-tuned models (e.g., LLaMA 3.1) generally exhibit **low baseline bias**, but subtle risks remain in chained setups.

---

## 📑 Table of Contents
- [Introduction](#-introduction)
- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Results](#-results)

---

## 📖 Introduction

**Prompt chaining** is a technique where outputs from one LLM step are used as inputs for the next. While this can improve reasoning and control, it raises questions about **bias amplification**.  

This project investigates:
1. How multi-step chaining affects bias propagation in LLMs.  
2. Which chain lengths minimize or amplify stereotypes.  
3. Which stereotype categories are most susceptible under chaining.  

---

## ✨ Features
- Direct vs. chained prompting experiments.  
- **Bias quantification** using **Jaccard similarity** on the StereoSet dataset.  
- Analysis by stereotype category (**gender, race, religion, profession**).  
- Chain progression tracking (bias at each step).  
- Configurable experiments (chain length, model, dataset splits).

---

## ⚙️ Installation

### Clone the repository
```
git clone https://github.com/<your-username>/Examining-Bias-in-LLM-Prompt-Chaining.git
cd Examining-Bias-in-LLM-Prompt-Chaining
```
### Create environment (pip)
```pip install -r requirements.txt```
### Or with Conda
```
conda env create -f environment.yml
conda activate llm-bias
```

---


## ▶️ Usage
### Run Direct Prompting (Baseline)
```python src/experiment_runner.py --mode direct --config configs/default.yaml```
### Run Chained Prompting
```python src/experiment_runner.py --mode chain --chain_length 3 --config configs/default.yaml```
### Analyze Results
```python src/analysis.py --results results/logs/experiment_run.json```

---

## 📊 Results (Summary)

Direct prompting produced low bias overall.

Chained prompting (2–3 steps) led to more neutral or anti-stereotypical outputs.

Longer chains (4+ steps) tended to amplify bias, especially in gender and profession.

<img width="737" height="491" alt="image" src="https://github.com/user-attachments/assets/aa26812e-506e-4b67-8eb4-a587f68018bb" />
