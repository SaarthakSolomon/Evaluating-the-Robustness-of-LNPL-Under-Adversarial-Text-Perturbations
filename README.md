# Auditing the Adversarial Robustness of LNPL in Text Classification: An Interpretability-Driven Analysis 

This repository accompanies my research titled:  
**"Auditing the Adversarial Robustness of LNPL in Text Classification: An Interpretability-Driven Analysis "**

This research investigates the adversarial robustness of the LNPL (Learning with Noisy and Pseudo Labels) training framework, originally designed for noisy label scenarios, by evaluating its behavior under semantically-preserving adversarial attacks in a sentiment classification task.

---

## 🧠 Project Overview

- **Dataset**: Yelp Polarity (50k balanced subset)
- **Model**: BERT-base-uncased fine-tuned with LNPL loss
- **Framework**: HuggingFace Transformers + TextAttack + SHAP
- **Goal**: Evaluate robustness of LNPL under word-level, char-level, and contextual perturbations
- **Key Techniques**:
  - Positive & Negative Training (LNPL)
  - Adversarial Attacks: TextFooler, DeepWordBug, TextBugger, BERT-Attack
  - SHAP-based Attribution Analysis

---

## 🗂️ Repository Structure

```
.
├── main.ipynb                    # End-to-end training + evaluation pipeline
├── requirements.txt              # Python dependencies
├── *.csv                         # Attack result logs (clean, baseline, LNPL variants)
├── SHAP.zip                      # SHAP attribution visualizations for failure cases   
```

---

## 🧪 Running the Project

### 1. Setup the Environment

```bash
git clone https://github.com/<your-username>/Evaluating-the-Robustness-of-LNPL.git
cd Evaluating-the-Robustness-of-LNPL
python -m venv venv
source venv/bin/activate   # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### 2. Run the Notebook

Open `main.ipynb` in Jupyter or VS Code to:

- Load Yelp dataset
- Tokenize & preprocess inputs
- Train LNPL-enhanced BERT model
- Evaluate under adversarial attacks
- Analyze failures using SHAP

---

## 📊 Result Files

Each attack logs both baseline and LNPL model outputs:

- `textfooler_baseline_results.csv`
- `textfooler_lnpl_results.csv`
- `deepwordbug_lnpl_results.csv`
- `bertattack_baseline_embedding_results.csv`
- ...and more

Each file typically includes:

- Original text
- Perturbed text
- Model predictions (before/after)
- Attack success/failure

---

## 🔍 SHAP Visualizations

The `SHAP.zip` file contains token-level attribution heatmaps comparing clean vs adversarial inputs for 10 representative failure cases.

These visualizations were used to derive the 3 failure modes discussed in Chapter 5:

- Surface Sensitivity
- Semantic Substitution Fragility
- Contextual Drift

---

## ❗ Notes

- Model checkpoints are **not included** to reduce repository size. The model can be retrained using the script provided.
- The project assumes access to a **GPU** for efficient training and attack execution.
- The Yelp Polarity dataset is assumed to be downloaded using `datasets.load_dataset("yelp_polarity")`.

---

## 📚 Citation / Credits

If referencing this work or extending LNPL under adversarial testing, please cite:

> Zhu, Z., Xu, J., Wang, Y., Sun, H., & Zhang, M. (2022).  
> *Towards Robust Learning with Noisy and Pseudo Labels for Text Classification.*  
> Information Sciences, 601, 1–17. https://doi.org/10.1016/j.ins.2024.120160

---

## 🧑‍🎓 Author

**Saarthak Solomon**    
[GitHub Profile](https://github.com/SaarthakSolomon)
