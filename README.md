# Data Notes — Medium Articles

**English** | [Türkçe](README.tr.md)

Code behind my data analysis, statistics and machine learning articles on Medium.
Each folder contains an executed Jupyter notebook that reproduces every chart and number in the related article from scratch.

> The articles are written in **Turkish**. The notebooks, charts and numbers can be followed without reading Turkish.

**Author:** Uğur Avşar · [Medium](https://medium.com/@uguravsar10) · [LinkedIn](https://www.linkedin.com/in/uguravsarr)

---

## Articles

| # | Article (Turkish title → English) | Topics | Code |
|---|--------|---------|-----|
| 01 | [Ortalama Yalan Söyler](https://medium.com/@uguravsar10/ortalama-yalan-s%C3%B6yler-grafi%C4%9Fe-bakmadan-karar-vermeyin-84ab115d802a) — *The Average Lies: Don't Decide Without Looking at the Chart* | Descriptive statistics · EDA · Data visualization · Data quality | [`01_ortalama_yalan_soyler`](01_ortalama_yalan_soyler/) |
| 02 | [Accuracy %99,9, Peki Model İşe Yarıyor mu?](https://medium.com/@uguravsar10/accuracy-99-9-peki-model-i%CC%87%C5%9Fe-yar%C4%B1yor-mu-dengesiz-veride-do%C4%9Fru-metrik-se%C3%A7imi-1583749e6dc8) — *99.9% Accuracy, but Does the Model Work? Choosing the Right Metric for Imbalanced Data* | Imbalanced data · Precision/Recall · ROC vs PR · Decision threshold | [`02_accuracy_yaniltir`](02_accuracy_yaniltir/) |
| 03 | [Yapay Zekâ İşleri mi Alıyor, Yoksa Sadece Suçu mu Üstleniyor?](https://medium.com/@uguravsar10/yapay-zek%C3%A2-i%CC%87%C5%9Fleri-mi-al%C4%B1yor-yoksa-sadece-su%C3%A7u-mu-%C3%BCstleniyor-71f44f79ce58) — *Is AI Taking Jobs, or Just Taking the Blame?* | Data validation · Time series · Bootstrap / Mann-Whitney · Power BI | [`03_ai_isten_cikarma`](03_ai_isten_cikarma/) |
| 04 | [Yağmur Yağdı, Barajlar Neden Dolmadı?](https://medium.com/@uguravsar10/ya%C4%9Fmur-ya%C4%9Fd%C4%B1-barajlar-neden-dolmad%C4%B1-i%CC%87stanbulun-suyunu-veriyle-okumak-898cf159f325) — *It Rained, So Why Didn't the Dams Fill? Reading Istanbul's Water with Data* | Time series · Seasonality · Questioning correlation · Data quality | [`04_istanbul_barajlari`](04_istanbul_barajlari/) |

---

## 01 · The Average Lies

![Cover](01_ortalama_yalan_soyler/gorseller/00_kapak.png)

📖 **[Read the article on Medium (Turkish)](https://medium.com/@uguravsar10/ortalama-yalan-s%C3%B6yler-grafi%C4%9Fe-bakmadan-karar-vermeyin-84ab115d802a)**

Three examples of why a single summary statistic (the mean, a correlation) can mislead:

1. **Taxi fares:** In a right-skewed distribution, the mean ($13.09) and the median ($9.50) differ; 70% of trips cost less than the average.
2. **Anscombe's quartet:** Four data sets with the same summary statistics and completely different charts.
3. **Tips:** 36% of trips show a zero tip; splitting by payment method reveals that cash tips are simply not recorded.

**Data**
- 6,433 taxi trips from March 2019, taken from NYC Taxi & Limousine Commission (TLC) records — [seaborn `taxis` sample data set](https://github.com/mwaskom/seaborn-data)
- Anscombe, F. J. (1973). *Graphs in Statistical Analysis.* The American Statistician, 27(1), 17–21.

---

## 02 · 99.9% Accuracy, but Does the Model Work?

![Cover](02_accuracy_yaniltir/gorseller/00_kapak.png)

📖 **[Read the article on Medium (Turkish)](https://medium.com/@uguravsar10/accuracy-99-9-peki-model-i%CC%87%C5%9Fe-yar%C4%B1yor-mu-dengesiz-veride-do%C4%9Fru-metrik-se%C3%A7imi-1583749e6dc8)**

Why accuracy can mislead on imbalanced data, and which measures to use to evaluate a classifier instead:

1. **The lazy model:** A model that calls every transaction "normal" scores 99.87% accuracy on the test set but catches no fraud at all.
2. **Three models compared:** Logistic regression catches 49% of fraud cases, the balanced model (class_weight="balanced") 88%; their accuracy is almost identical.
3. **ROC vs. Precision–Recall:** For the same model, ROC-AUC is 0.97 while average precision is 0.71.
4. **Decision threshold:** When the threshold is chosen by cost with time-ordered cross-validation on the training data, the total cost on the test set falls by about 60% (under the stated assumptions).

**Data**
- Credit card fraud data set — 284,807 transactions by European cardholders over two days in September 2013 (492 frauds). ULB Machine Learning Group & Worldline; "Credit Card Fraud Detection" on Kaggle. The notebook uses a public GitHub copy of the data (~100 MB).
- Dal Pozzolo, A., Caelen, O., Johnson, R. A. & Bontempi, G. (2015). *Calibrating Probability with Undersampling for Unbalanced Classification.* IEEE SSCI, 159–166.

---

## 03 · Is AI Taking Jobs, or Just Taking the Blame?

![Cover](03_ai_isten_cikarma/gorseller/00_kapak.png)

📖 **[Read the article on Medium (Turkish)](https://medium.com/@uguravsar10/yapay-zek%C3%A2-i%CC%87%C5%9Fleri-mi-al%C4%B1yor-yoksa-sadece-su%C3%A7u-mu-%C3%BCstleniyor-71f44f79ce58)**

The story of my Softito Data Analytics capstone project: 643 layoff announcements from 2026, checked against news sources, to see how often companies actually cited AI and what happened in job postings at the same time:

1. **Data validation:** 146 rows checked by hand; 4 wrong-year announcements excluded, 2 numbers corrected.
2. **Strict vs. broad definition:** 16.9% of people were in announcements where the company clearly cited AI; counting every AI label gives an upper bound of 38.4%.
3. **Monthly trend:** AI as a stated reason peaked in May (40% of announcements) and fell to about 3–6% from August.
4. **Size:** The median AI-attributed announcement covers 295 people, others 180 (95% bootstrap CI for the difference: 50–421).
5. **Hiring side:** The share of US job postings mentioning AI rose from 3.6% to 7.2% in one year (not a cause-and-effect claim).

**Data**
- Cleaned project files: [Uguravsar75/ai-layoffs-vs-hiring-2026](https://github.com/Uguravsar75/ai-layoffs-vs-hiring-2026)
- layoffhedge.com 2026 layoff list (version of 8 November 2026) · Indeed Hiring Lab AI Tracker (CC BY 4.0) · Challenger, Gray & Christmas monthly reports

---

## 04 · It Rained, So Why Didn't the Dams Fill?

![Cover](04_istanbul_barajlari/gorseller/00_kapak.png)

📖 **[Read the article on Medium (Turkish)](https://medium.com/@uguravsar10/ya%C4%9Fmur-ya%C4%9Fd%C4%B1-barajlar-neden-dolmad%C4%B1-i%CC%87stanbulun-suyunu-veriyle-okumak-898cf159f325)**

Istanbul's dam occupancy, rainfall over the basins and water consumption, using İBB open data:

1. **Drought periods:** Between 2005 and 2021, occupancy fell below 30% in 2007–2008, 2014 and 2020–2021 (638 days in total; lowest 9.2%, November 2007).
2. **Annual cycle:** 53.9% of rain falls between November and March; dams peak in April and bottom out in November; consumption is highest in July.
3. **2014:** Rainfall over the water year was above average, but the winter was the driest in nine years; the dams fell to 14.5% on 16 September 2014.
4. **Questioning correlation:** The 0.62 correlation between winter rainfall and the spring peak comes largely from 2014; without 2014 it is −0.04.
5. **Consumption:** Average daily consumption rose 35.6% from 2011 to 2023 and did not fall in any year.

**Data**
- İBB Open Data Portal (İSKİ data): dam occupancy rate (2005–2021), basin rainfall and daily water consumption (2011–2024). Raw files: [Uguravsar75/istanbul-baraj-analizi](https://github.com/Uguravsar75/istanbul-baraj-analizi)

---

## How to run

```bash
git clone https://github.com/Uguravsar75/medium-makaleler.git
cd medium-makaleler
pip install -r requirements.txt
jupyter notebook   # open any notebook from the folders
```

The notebooks read their data directly from the internet; no separate download is needed.
