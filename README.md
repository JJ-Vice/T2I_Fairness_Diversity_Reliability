# On the Fairness, Diversity and Reliability of Text-to-Image Generative Models
### First Author / Maintainer: Jordan Vice
![Screenshot from 2025-05-06 14-10-36](https://github.com/user-attachments/assets/d9e3b2e4-6a36-47bd-9461-acb4c94ee426)

This repository provides an evaluation suite for probing **reliability**, **fairness**, and **diversity** in text-to-image generative models. The methods are designed to detect biased behaviors, measure robustness to embedding perturbations, and retrieve the provenance of unreliable or manipulated outputs.

---

## 📖 Overview

Multimodal generative models like Stable Diffusion and DALL·E are widely used, but often act unpredictably due to learned or injected biases. This repository proposes a **training-free, evaluation-only framework** to:

- Detect unreliable behavior via **global and local perturbations** in the embedding space.
- Measure **generative diversity** to assess representational spread.
- Quantify **generative fairness**, i.e., how much influence individual tokens exert on output.
- Identify **bias triggers** and trace their origin in intentionally-biased models.

Our framework supports both **benign and intentionally-biased** text-to-image models.

---

## 🧪 Notebooks and Their Purpose

| Notebook                     | Purpose |
|-----------------------------|---------|
| `global_reliability_eval.ipynb` | Evaluates model reliability by applying **global perturbations** across entire text embeddings. Helps identify prompts that yield sensitive or unstable outputs. |
| `local_reliability_eval.ipynb`  | Applies **token-level (local) perturbations** to reveal which specific words disproportionately affect generation. |
| `diversity_eval.ipynb`          | Measures **image diversity** from a single concept or token using cosine similarity. Low diversity may indicate biased or overly deterministic behavior. |
| `fairness_eval.ipynb`           | Assesses **generative fairness** by removing tokens and observing how significantly the output changes under **low-guidance** generation settings. |

---

## 🧰 Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/text2image-fairness-eval.git
   cd text2image-fairness-eval
   ```
2. **Create and activate a virtual environment**
   ```bash
   conda create -n t2i-fairness python=3.9.16
   conda activate t2i-fairness
   ```
3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
5. **Download model/model weights**

You'll need access to a Stable Diffusion model and its tokenizer/CLIP encoder. You can obtain them from HuggingFace (e.g., CompVis/stable-diffusion-v1-4) and load using diffusers or transformers.


## 📜 Extended Description

From the manuscript:

*We propose a reliability evaluation framework for text-to-image generative models that leverages embedding-space perturbations to assess both global and local sensitivity. If a model produces visually different images in response to small changes in the embedding space, it is deemed unreliable. We build upon this by introducing fairness and diversity evaluations to characterize model behavior when exposed to sensitive tokens or prompts. Fairness measures the degree of influence that individual tokens have over generation under low-guidance settings. Diversity evaluates whether outputs for a given concept are meaningfully varied. These metrics enable the detection and retrieval of bias triggers, particularly in models that have been intentionally manipulated via backdoor attacks or unfair training paradigms. Our method is entirely inference-based (no model retraining required) and applicable in both grey-box and black-box settings. We offer a modular and reproducible toolset to audit generative models for ethical AI concerns including bias, trustworthiness, and misuse.*

## 🖇️ Citation

If you use this work, please cite the associated paper:

```bib
@misc{vice2024fairness,
      title={On the Fairness, Diversity and Reliability of Text-to-Image Generative Models}, 
      author={Jordan Vice and Naveed Akhtar and Richard Hartley and Ajmal Mian},
      year={2024},
      eprint={2411.13981},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2411.13981}, 
}
```
