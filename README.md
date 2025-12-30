# 📊 Data Processing and Machine Learning Models for Phosphor Prediction

This repository contains the data preprocessing pipeline and machine learning models used in our study on **composition-based prediction of doped phosphor materials**. The workflow is designed to be **simple, reproducible, and fully based on elemental composition**, without relying on complex structural descriptors.

## 🔧 Data Processing

### Input Data

* Experimental datasets collected from the literature
* Each entry includes:

  * Chemical composition
  * Excitation wavelength
  * Emission wavelength
  * Crystal field energy levels (⁴T₁, ⁴T₂)

### Composition Representation

Raw chemical formulas of the form:

[
A_x B_y C_{z-t} \cdots Mn_t
]

are transformed into a **normalized compositional format**:

[
A_a B_b C_c \cdots Mn_{mn}
]

where:

* (a, b, c, mn) are **atomic percentages**
* (\sum a_i = 100%)
* Each material is encoded as a **fixed-length vector (44 features)** corresponding to all possible elements
* Absent elements are assigned a value of **0**

This representation is often referred to as **distributional (composition-only) data**.

---

## 🌲 Machine Learning Model: Extra Trees Regressor

* Algorithm: `ExtraTreesRegressor` (scikit-learn)
* Input: Normalized elemental composition (44 features)
* Output: Emission wavelength

### Evaluation
Performance is evaluated using:

* Coefficient of determination ((R^2))
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)

---

## 🔍 Feature Importance

The Extra Trees model provides intrinsic feature importance scores, enabling analysis of:

* Which elements most strongly influence emission wavelength
* How host chemistry affects crystal field strength

This enhances **model interpretability** and links predictions to physical mechanisms.

