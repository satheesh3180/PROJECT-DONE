# PROJECT-DONE

# Advanced Causal Inference with Double Machine Learning (DML)

#  Project Overview

This project implements an **Advanced Double Machine Learning (DML)** framework to estimate causal treatment effects in the presence of **high‑dimensional confounding variables**. The goal is to demonstrate how DML outperforms traditional regression (OLS) when treatment assignment and outcomes are nonlinear and confounded.

The implementation closely follows the methodology proposed by **Chernozhukov et al.**, using cross‑fitting and machine learning models for nuisance parameter estimation.

---

#  Objectives

* Generate a **synthetic dataset** with:

  * 5,000 samples
  * 100 high‑dimensional confounders
  * Binary treatment variable
  * Continuous outcome variable
  * Non‑constant (heterogeneous) treatment effect
* Implement **Double Machine Learning (DML)** with cross‑fitting
* Compare DML against a **baseline OLS regression**
* Quantitatively evaluate **bias reduction**
* Visualize **heterogeneous treatment effects (HTE)**

---

#  Dataset Description

* **X**: 100‑dimensional confounder matrix sampled from a normal distribution
* **T**: Binary treatment assigned via a nonlinear, confounded logistic function
* **Y**: Continuous outcome influenced by treatment, confounders, and noise
* True Treatment Effect 

  * Depends nonlinearly on confounders
  * Ensures heterogeneity across samples

This design intentionally violates linear modeling assumptions, making it ideal for testing DML.

---

#  Methodology

#  Double Machine Learning (DML)

* **Cross‑fitting** with 5 folds to avoid overfitting bias
* **Nuisance models**:

  * Outcome model: RandomForestRegressor
  * Treatment model: RandomForestClassifier
* Residualization of outcome and treatment
* Final stage: Linear regression of residualized outcome on residualized treatment

This approach orthogonalizes nuisance errors, yielding a robust ATE estimate.

---

# Baseline: Ordinary Least Squares (OLS)

* Linear regression of outcome on treatment and all confounders
* Serves as a naive baseline under model misspecification

---

#  Results Summary

| Metric              | Value                           |
| ------------------- | ------------------------------- |
| True ATE            | Computed from ground‑truth τ(x) |
| Estimated ATE (DML) | Close to true ATE               |
| Estimated ATE (OLS) | Noticeably biased               |
| DML Bias            | Significantly lower             |
| OLS Bias            | Higher due to confounding       |

 **Key Insight:** DML substantially reduces bias compared to OLS in high‑dimensional nonlinear settings.

---

#  Visualization

* Scatter plot showing **true heterogeneous treatment effects** against a key confounder
* Horizontal line representing **DML estimated ATE**

This visualization confirms:

* Treatment effects vary across individuals
* DML successfully captures the *average* causal effect despite heterogeneity

---

#  Technologies Used

* Python
* NumPy, Pandas
* Scikit‑learn
* Matplotlib

---

#  Conclusion

This project demonstrates that:

* Traditional OLS struggles under nonlinear confounding
* Double Machine Learning provides **robust and unbiased causal estimates**
* Cross‑fitting with machine learning models is critical for valid inference

 *DML is a powerful framework for modern causal inference problems involving complex, high‑dimensional data.**

---

# Future Improvements

* Extend to **Conditional Average Treatment Effect (CATE)** estimation
* Compare with other causal methods (IPW, DR Learner, Causal Forests)
* Apply to real‑world observational datasets

---

###  Project Status: **Completed Successfully**
