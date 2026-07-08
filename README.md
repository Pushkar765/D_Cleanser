# 🎩 The Data Cleanser — A Most Proper Treatise on Tidy Data

*Being a faithful account of how one might set right a dataset most unruly, rendered in olde English fashion for thine amusement and edification.*

---

## 📜 Preamble

Good morrow, gentle reader! Herein lies a jolly good notebook, christened `D-Cleanser.ipynb`, wherein a dataset of patient health — rather blemished with gaps and unruly outliers — is coaxed back into respectable order. Pray, take a seat by the hearth and allow this humble document to guide thee through the proceedings.

---

## 🏛️ Part A — On the Handling of Missing Values

'Tis a common affliction, dear reader, for a dataset to be riddled with absences most vexing — empty cells where numbers ought to dwell. This section doth undertake the following noble tasks:

- **A survey of the missing**: identifying which columns art most afflicted, and reckoning the percentage of their emptiness, presented most handsomely in a bar-chart.
- **Sundry methods of imputation** are then trialed, each with its own particular virtue:
  - **Mean Imputation** — for the `bmi` column, filling gaps with the average, as befits a symmetric distribution.
  - **Most Frequent Imputation** — bestowed upon `region` and `gender`, categorical columns each possessed of one dominant sort.
  - **Missing Indicator** — a most clever device, marking which values were once absent, lest we forget.
  - **Random Sample Imputation** — drawing replacement values at random from what remaineth.
  - **K-Nearest Neighbours (KNN) Imputation** — the cleverest of the lot, filling gaps by consulting a patient's similar neighbours across `age`, `bmi`, `blood_pressure`, `cholesterol`, and `glucose`.
  - **Iterative Imputation (MICE)** — a most sophisticated technique, modelling each column in turn upon the others.

---

## 🏚️ Part B — On the Matter of Outliers

Some values, dear reader, are simply *not to be trusted* — extreme numbers that skulk about the fringes of respectability. This section doth detect and dispatch them by several honourable methods:

- **The Z-Score Method** — reckoning how many standard deviations a value strayeth from the mean, applied unto `cholesterol` and `glucose`.
- **The Interquartile Range (IQR) Method** — a more discerning approach, applied unto `bmi`, catching five outliers most impertinent.
- **The Percentile Method** — capping values beneath the 5th and above the 95th percentile, the most aggressive of the three.
- **Winsorization** — rather than banishing outliers outright, this method merely *tempers* their extremity, preserving the full company of the dataset whilst curbing their influence.

---

## 🏰 Part C — The Final Clean Dataset

Once the dataset hath been thoroughly scrubbed and set in order, it is exported unto several `.csv` files for posterity:

| File | Contents |
|---|---|
| `df_mean.csv` | Data with mean imputation applied |
| `df_frequent.csv` | Data with most-frequent imputation applied |
| `df_final.csv` | Data with missing indicators included |
| `df_imputed.csv` | Data following KNN/MICE imputation |
| `df_clean_by_Outliers.csv` | Data cleansed by the IQR method |
| `df_clean_bmi.csv` | Data cleansed by the Percentile method |

---

## 📝 A Brief Report, Most Considered

**Which imputation strategy proved most effective?**
Mean imputation served `bmi` well enough, it being fairly symmetric, though median would suit a skewed column better. For categorical columns, Most Frequent imputation was simplest and clearest. Yet the KNN Imputer proved the finest of all, for it consulted a patient's fellow health metrics rather than filling gaps in blind isolation.

**Which method of outlier-handling best preserved the quality of the data?**
The Z-score method was found too lenient, catching naught. The IQR method caught five outliers in `bmi`, whilst the Percentile method was the most zealous of all. Winsorization, however, preserved matters best — capping extremity without banishing a single patient from the record.

**How did this cleansing improve the dataset's usability?**
All gaps in `age`, `bmi`, `region`, `gender`, `cholesterol`, and `glucose` were duly filled. Extreme `bmi` values were either removed or tempered, sparing the mean and any downstream model from distortion. The dataset now standeth complete, consistent, and fit for further study — including the noble pursuit of predicting `disease_risk`.

---

## 🔧 Requirements, for Those Who Wish to Follow Suit

```
numpy
pandas
matplotlib
seaborn
scikit-learn
```

## ▶️ How One Might Run This Notebook

1. Procure `patient_health.csv` and place it alongside the notebook.
2. Install the aforementioned requirements: `pip install numpy pandas matplotlib seaborn scikit-learn`
3. Open `D-Cleanser.ipynb` in Jupyter, and proceed through it cell by cell, as a gentleman or gentlewoman of leisure might peruse a favourite novel.

---

*Thus concludes this account. May thy data ever be tidy, and thy outliers ever tempered.* 🕰️
