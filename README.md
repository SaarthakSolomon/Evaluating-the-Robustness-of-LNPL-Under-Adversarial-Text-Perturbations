# Auditing the Adversarial Robustness of LNPL in Text Classification: An Interpretability-Driven Analysis

This repository contains the implementation and experimental artifacts accompanying the paper:

**“Auditing the Adversarial Robustness of LNPL in Text Classification: An Interpretability-Driven Analysis.”**

This work evaluates the adversarial robustness of the **Learning with Noisy and Pseudo Labels (LNPL)** framework—originally proposed for learning under label noise—by auditing its behavior under **semantically preserving adversarial attacks** in a sentiment classification setting.

---

## 🧠 Overview

- **Task**: Binary sentiment classification  
- **Dataset**: Yelp Polarity (50K balanced training subset)  
- **Model**: BERT-base-uncased fine-tuned with LNPL loss  
- **Frameworks**: Hugging Face Transformers, TextAttack, SHAP  
- **Objective**: Assess whether robustness to label noise transfers to robustness against adversarial input perturbations  

### Key Techniques

- Positive Training and Negative Training (LNPL)
- Adversarial Attacks:
  - TextFooler
  - DeepWordBug
  - TextBugger
  - BERT-Attack (Masked LM and Embedding variants)
- SHAP-based token-level attribution analysis for failure diagnosis

---

## 🗂️ Repository Structure

.
├── main.ipynb # End-to-end training, evaluation, and analysis pipeline
├── requirements.txt # Python dependencies
├── *.csv # Adversarial attack result logs (baseline and LNPL)
├── SHAP.zip # SHAP attribution visualizations for representative failure cases

yaml
Copy code

---

## 🧪 Reproducing the Experiments

### Environment Setup

```bash
git clone https://github.com/SaarthakSolomon/Auditing-the-Adversarial-Robustness-of-LNPL-in-Text-Classification-An-Interpretability-Driven-Analy.git
cd Auditing-the-Adversarial-Robustness-of-LNPL-in-Text-Classification-An-Interpretability-Driven-Analy
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```
## 🧪 Running the Pipeline

Open `main.ipynb` to:

- Load the Yelp Polarity dataset  
- Preprocess and tokenize inputs  
- Train a BERT classifier with LNPL loss  
- Generate adversarial examples using TextAttack  
- Evaluate robustness metrics  
- Analyze failure cases using SHAP  

---

## 📊 Experimental Outputs

Each adversarial attack logs model behavior for both baseline BERT and LNPL-trained models. Example files include:

- `textfooler_baseline_results.csv`
- `textfooler_lnpl_results.csv`
- `deepwordbug_lnpl_results.csv`
- `bertattack_embedding_results.csv`

Each result file typically contains:

- Original input text  
- Adversarially perturbed text  
- Model predictions (clean vs. adversarial)  
- Attack success indicators  

---

## 🔍 SHAP Attribution Analysis

The `SHAP.zip` archive contains token-level attribution heatmaps comparing clean and adversarial inputs for **10 representative failure cases**.

These visualizations support the failure mode taxonomy discussed in the paper:

- Surface Sensitivity  
- Semantic Substitution Fragility  
- Contextual Drift  

---

## ❗ Notes

- Model checkpoints are **not included** to keep the repository lightweight. All models can be retrained using the provided pipeline.
- A **GPU is recommended** for efficient training and adversarial attack execution.
- The Yelp Polarity dataset is loaded via:

```python
datasets.load_dataset("yelp_polarity")
```
📚 Citation

If you use or extend this work, please cite:

Zhu, Z., Xu, J., Wang, Y., Sun, H., & Zhang, M. (2022).
Towards Robust Learning with Noisy and Pseudo Labels for Text Classification.
Information Sciences, 601, 1–17.
https://doi.org/10.1016/j.ins.2024.120160

🧑‍💻 Author

Saarthak Solomon
GitHub: https://github.com/SaarthakSolomon
