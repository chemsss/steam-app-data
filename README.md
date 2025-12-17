# Steam Game Hit Prediction – Data Science Project

## 📌 Overview

This repository contains a **Data Science project** focused on predicting whether a video game released on **Steam** can be considered a *hit* based on its characteristics (metadata, genres, languages, tags, etc.) and using the [IMDb Top 250 ranking weighted rating formula](https://help.imdb.com/article/imdb/track-movies-tv/ratings-faq/G67Y87TFYYP6TWAV#).

The project follows a classic end-to-end **machine learning pipeline**, from data cleaning and feature engineering to model training and evaluation.

The work is organized into **two Jupyter notebooks**, each with a clear and complementary purpose.

---

## Dataset Source

The raw dataset **`steam_app_data.csv`** is not included in this repository because it is too large for GitHub.

You must download it manually from the original Kaggle source:

* [https://www.kaggle.com/datasets/fmpugliese/steam-all-games-data](https://www.kaggle.com/datasets/fmpugliese/steam-all-games-data)

Once downloaded, place the file in the following directory:

```
dataset/steam_app_data.csv
```

This file is required to run the data cleaning and feature engineering notebook.

---

## How to Run the Project

1. Clone the repository
2. Install dependencies:

   ```bash
   pip install pandas numpy scikit-learn jupyter
   ```
3. Download `steam_app_data.csv` from Kaggle and place it in `dataset/`
4. Run the notebooks **in order**:

   1. `data_cleaning_and_engineering.ipynb`
   2. `training_and_evaluation.ipynb`

---

## Repository Structure

```
├── data_cleaning_and_engineering.ipynb
├── training_and_evaluation.ipynb
├── dataset/
│   └── all_data.csv
├── steam_dataset_clean.csv
└── README.md
```

> ⚠️ The raw dataset (`all_data.csv`) is expected to be placed in the `dataset/` folder.

---

## Notebooks Description

### 1️⃣ `data_cleaning_and_engineering.ipynb`

This notebook is dedicated to **data preparation** and **feature engineering**. It includes:

* Loading the raw Steam dataset
* Handling missing values and inconsistencies
* Cleaning textual and categorical features
* Feature engineering on complex columns (e.g. genres, tags, supported languages)
* Encoding multi-label features using techniques such as `MultiLabelBinarizer`
* Creation of the target variable (`is_hit`)
* Export of a clean and ready-to-use dataset: `steam_dataset_clean.csv`

📤 **Output**: a cleaned dataset used for modeling

---

### 2️⃣ `training_and_evaluation.ipynb`

This notebook focuses on **machine learning modeling** and **performance evaluation**:

* Loading the cleaned dataset
* Train / test split
* Feature scaling where necessary
* Training classification models
* Model comparison
* Evaluation using appropriate metrics:

  * F1-score
  * Fβ-score
  * Accuracy (when relevant)

🎯 **Objective**: predict whether a game is a *hit* (`is_hit = 1`) or not (`is_hit = 0`).

---

## 🧠 Target Variable

* **`is_hit`**: binary classification label indicating whether a Steam game is considered a hit.

The exact definition of a *hit* (thresholds, business logic) is documented and implemented directly in the data preparation notebook.  

### Weighted Rating Formula

![image](https://s3.eu-west-1.amazonaws.com/images.tutorialedge.net/images/python/recommender-system-python/image2-19.png "IMDb Top 250 ranking weighted rating formula")  

Where:

- **R** = average rating for the title  
- **v** = number of ratings for the title  
- **m** = minimum number of ratings required to be listed in the Top Rated 250 chart (currently 25,000)  
- **C** = mean rating across the whole report


---

## Technologies & Libraries

* Python 3
* pandas
* NumPy
* scikit-learn
* Jupyter Notebook
