# 🏋️‍♂️ Push-Up Prediction from Smartphone & Smartwatch Sensor Data

[![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white&style=flat)](https://www.python.org/)  
[![Random Forest](https://img.shields.io/badge/-Random%20Forest-006400?style=flat)](https://en.wikipedia.org/wiki/Random_forest)

## 📘 Project Summary
As part of the **ML for the Quantified Self** course at Vrije Universiteit Amsterdam, I worked with two teammates to predict the **number of push-ups done in the last 10 seconds** using wearable sensor data. We evaluated various machine learning models, focusing on Random Forests, and performed extensive preprocessing, feature engineering, and statistical evaluation.

We received a final grade of **9.5/10** for this assignment.

---

## 👋 What I Did

- Collected and processed time-series data from iPhone and Apple Watch sensors
- Merged multiple sensors (e.g., accelerometer, gyroscope, gravity, magnetometer, orientation, barometer, heart rate)
- Imputed missing values, performed backfilling on annotation columns
- Conducted exploratory data analysis and outlier inspection
- Applied **Fourier Transform** and created spectrograms to analyze frequency patterns
- Engineered clustering-based features based on sensor correlations
- Trained and evaluated several ML models: **Random Forest**, Decision Tree, SVM, NN, Gradient Boosting, Naive Bayes
- Statistically evaluated results using **ANOVA** and **Bonferroni correction**

---

## 🧠 Dataset
- Sensor data collected from smartphone and smartwatch during push-up activity (40+ mins)
- 48 original features → processed to 11990 time-aligned rows (resampled at 200ms)
- Final model input aggregated to **240 rows** (10s windowed push-up counts)

![Sensor EDA](https://i.imgur.com/rbwdAzC.png)

### 🧹 Preprocessing Steps
- Annotation backfilling
- Linear interpolation of NaNs
- Fourier Transform (DFT) over rolling time windows
- Dimensionality reduction through correlation filtering
- Clustering (K-Means) based on most correlated signals

![Clustering Results](https://i.imgur.com/LRr5aVg.png)


---

## 📈 Models Compared

| Model             | Type         | Notes                          |
|------------------|--------------|--------------------------------|
| Average Baseline | Baseline     | Predicts the mean              |
| Linear Regression| Regression   | High variance observed         |
| Random Forest     | Ensemble     | 🌟 Best overall performance     |
| Decision Tree    | Tree         | Best single run (low MAE)      |
| Neural Network   | MLP          | Logistic activation            |
| SVM              | Kernel-based | Moderate results               |
| Naive Bayes      | Probabilistic| High error                     |
| Gradient Boosting| Ensemble     | Competitive but lower than RF |

---

## 🥇 Results

### 📊 Metrics (over 18 iterations)
- **Random Forest** achieved the best **average** performance:
  - MSE: ✅ Significantly lower than almost all other models
  - MAE: ✅ Low, though DT had slightly better average
  - R²: ✅ Highest explained variance

```text
ANOVA Results (p-values):
- MSE: p = 0.001
- MAE: p < 0.001
- R² : p < 0.001
```
![Model Comparison](https://i.imgur.com/SKobf2V.png)
### 🔬 Key Findings
- **RF significantly outperformed** all models except Decision Trees and Bagging Regressor
- Clustering features helped separate light vs. intense push-up sets
- Best single-run model: Decision Tree with MAE = 0.28 and R² = 0.89

![Model Comparison](https://github.com/JoshuaSeth/MLQS/raw/master/figs/performance_boxplot.png)

---

## 🧩 Takeaways
- Proper signal synchronization and feature engineering were crucial
- Frequency-domain data revealed useful structure for movement prediction
- Ensemble methods like Random Forest generalize well under noisy, real-world settings
- Dataset size was limited to one participant — future work should expand to multi-user settings

---

## 🎓 Grade: **9 / 10**  
Course: *Machine Learning for the Quantified Self — Vrije Universiteit Amsterdam*

<p align="center">Made with 📱 sensors, ⏱️ time windows, and 🌲 lots of Random Forests</p>
