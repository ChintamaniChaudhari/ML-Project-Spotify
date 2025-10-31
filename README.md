# 🎵 Spotify Hit Song Predictor: A Musician's ML Co-Pilot

![Streamlit App](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit)
![Python 3.11+](https://img.shields.io/badge/Python-3.11%2B-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![XGBoost](https://img.shields.io/badge/XGBoost-Optimized-brightgreen)

**Project by: Chintamani Chaudhari (PRN: 22070521138)**
**Course: Machine Learning Mini Project (CA4)**

This is the repository for my end-to-end Machine Learning project. This project analyzes a dataset of 6,400 Spotify songs from the 2010s to build a "Musician's Co-Pilot"—a 3-part toolkit to help artists make data-driven decisions during the songwriting process.

## 🚀 The Final Application
The primary output is a live web application built with Streamlit.

**(Note: Add your best screenshot, like `image_749ba0.jpg`, to your repository and this image will load)**
![Screenshot of the Streamlit App]([image_749ba0.jpg](https://github.com/user-attachments/assets/ccb60471-dabb-44cf-a00f-f5be5d34b969))

---

## 🎯 The Problem & The Need

### The Problem
For a musician or record label, the success of a new song is a "black box." Millions are invested into producing and promoting tracks with no guarantee of success. It's difficult to know what separates a "Hit" from a "Flop" and even harder to know how to *fix* a song that isn't performing well.

### The Need
Musicians need a data-driven toolkit that goes beyond a simple "yes/no" prediction. They need **actionable insights** to:
1.  **Forecast** a new song's potential before it's released.
2.  Get **guidance** on *how to improve* a song that is predicted to be a "Flop."
3.  Understand the **underlying "formulas"** that successful songs share.

---

## 💡 Our Solution: The "Musician's Co-Pilot"
This project is built as a 3-part toolkit, with each model solving the next logical problem for a musician.

### 1. The Predictor (Classification)
* **Question:** "Will my new song be a 'Hit' or a 'Flop'?"
* **Logic:** Our **EDA** (`ML_EDA_22070521138.ipynb`) showed that no single feature (like `energy` or `loudness`) could predict a hit. This proved we needed an advanced model.
* **Solution:** We built and tuned multiple models (`Classification Model Selection.ipynb`). The winner was a **Tuned XGBoost Classifier** that achieved an **85.3% F1-Score**. This is the "brain" inside our Streamlit app.

### 2. The Engineer (Regression)
* **Question:** "My song is a 'Flop'. How do I *fix* it?"
* **Logic:** The "Predictor" model's feature importance plot (`image_18073f.png`) showed that **`danceability`** is one of the *most critical* features for a hit. However, a musician can't "turn up a danceability knob"—it's an *outcome* of other features they *can* control (like `tempo`, `energy`, etc.).
* **Solution:** We built an **XGBoost Regressor** (`ML Regression.ipynb`) that predicts a song's `danceability` based on its other features with **77% R-Squared accuracy**. This allows a musician to use it as a "what-if" engine to see how tweaking their song's mix can improve its danceability.

### 3. The Formula (Clustering)
* **Question:** "What *are* the secret formulas I'm aiming for?"
* **Logic:** Our EDA plots (`image_328fc2.png`, `image_328fe2.png`) showed that songs are not all one type (e.g., `instrumentalness` is mostly zero, `acousticness` has two peaks). This proves there are hidden groups.
* **Solution:** We used **K-Means Clustering** (`ML Clustering.ipynb`) to analyze all 6,400 songs. The model discovered **4 distinct "song formulas"**:
    * **Formula A ("The Standard Hit"):** 57% Hit Rate. High energy, loud, standard structure.
    * **Formula B ("The Simple Hit"):** 53% Hit Rate. High danceability, loud, *simple* structure.
    * **Formula C ("The Niche Flop"):** 17% Hit Rate. Quieter, more complex (e.g., Jazz, Ambient).
    * **Formula D ("The Super-Flop"):** 4% Hit Rate. Very quiet, *very* complex (e.g., Metal, Live Jazz).

---

## 🚀 How to Run This Project

### 1. Run the Web App (Recommended)
This is the easiest way to see the project's main outcome.

**Prerequisites:**
* Python 3.9+
* The following files from this repository:
    * `ML.py`
    * `hit_classifier.joblib`
    * `scaler.joblib`
    * `background.jpg`

**Installation:**
```bash
# 1. Clone this repository
git clone [https://github.com/ChintamaniChaudhari/ML-Project-Spotify.git](https://github.com/ChintamaniChaudhari/ML-Project-Spotify.git)
cd ML-Project-Spotify

# 2. Install the required libraries
# (It's recommended to use a virtual environment)
pip install streamlit pandas numpy scikit-learn xgboost joblib

# 3. Run the Streamlit app!
streamlit run ML.py
