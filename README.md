# Lung Cancer Survival Analysis

This repository contains a survival analysis project predicting the survival duration (in days) of patients with lung cancer, based on their 3D CT scans and associated meta-data. The project is inspired by [scikit-survival](https://scikit-survival.readthedocs.io/en/stable/user_guide/index.html) and leverages multiple survival models.

This project was part of the Bio AI hackathon from Entrepreneur First 2024 in December, proposed by Owkin.

## Project Overview

The objective of this project is to develop a machine learning pipeline to predict the survival outcomes of lung cancer patients. By combining 3D CT imaging data with patient meta-data, we aim to improve the accuracy of survival prediction models.

Each patient record in the dataset consists of:
- A set of covariates $x \in \mathbb{R}^d$, representing patient-specific features.
- The event time $t > 0$, which marks when an event (e.g., death) occurred.
- The censoring time $c > 0$, which represents when the observation was censored (i.e., the event was not observed within the study period).

Since an event occurrence and censoring are mutually exclusive, an event indicator $\delta \in \{0,1\}$ is defined:
- $\delta = 1$ if the event occurred (i.e., $t$ is observed).
- $\delta = 0$ if the observation is censored (i.e., $c$ is observed instead).

## Observable Survival Time
The observed survival time $y$ for a right-censored sample is defined as:

$$
y = \min(t, c) = \begin{cases}
t, & \text{if } \delta = 1, \\
c, & \text{if } \delta = 0.
\end{cases}
$$

## Importance in Modeling
Survival analysis models need to account for the unique characteristics of censored data. Standard regression models are not suitable because they do not handle the partial observation of event times correctly. The methods used in survival analysis consider both the observed event times and the censoring mechanism to make accurate predictions and inferences.

This repository explores different models that address these challenges effectively.

## Models Used

The analysis leverages several survival models, including:

- **Survival Random Forest (RSF)**
- **Survival XGBoost (sXGB)**
- **Survival Support Vector Machine (SSVM)**
- **DAFT (Deep Attentive Feature-based Tabular) model**: Interweaving 3D CT scan images with tabular meta-data for enhanced predictive performance.

These models are implemented using the `scikit-survival` and `scikit-learn` libraries, which provide an efficient and easy-to-use framework for survival analysis.

## Data

The dataset consists of:

- **3D CT scans**: Preprocessed to extract relevant imaging features.
- **Meta-data**: Patient demographics, clinical characteristics, and follow-up information.

## Project Structure

```
├── data/
│   ├── ct_scans/
│   ├── eda.csv
│   ├── meta_data.csv
├── notebooks/
│   ├── daft_model.ipynb
│   ├── survival_models.ipynb
├── README.md
```

## Installation

Clone the repository and install the required dependencies:

```bash
git clone https://github.com/AlexBoving/survival-analysis-lung-cancer.git
```

## Usage

1. **Data Preparation:** Ensure that CT scans are placed in the `data/ct_scans/` folder and meta-data is correctly formatted in `data/meta_data.csv`.
2. **Exploratory Data Analysis:** Run `notebooks/eda.ipynb` to explore and visualize the dataset.
3. **Model Training & Evaluation:** Train and evaluate survival models with `notebooks/daft_model.ipynb` and `notebooks/survival_models.ipynb`.

## Results

The models are evaluated based on the concordance index (C-index).

## Acknowledgements

This project is heavily inspired by the excellent documentation and tools provided by the [scikit-survival](https://scikit-survival.readthedocs.io/en/stable/user_guide/index.html) library.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ Feel free to contribute or open issues for any suggestions or improvements!
