# Sentiment Analysis with R — NLP Teaching Notebook

> An educational Jupyter Notebook introducing R programming and NLP-based sentiment analysis using the AFINN lexicon — developed during a Research Assistant role at the College of Business, Michigan Technological University.

![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Language](https://img.shields.io/badge/Language-R-276DC3)
![Role](https://img.shields.io/badge/Role-Research%20Assistant%20%40%20MTU-darkgreen)
![Tools](https://img.shields.io/badge/Tools-tidytext%20%7C%20dplyr%20%7C%20tidyverse%20%7C%20AFINN-orange)

---

## 📌 Project Overview

This notebook was developed as part of a **Research Assistant** position at the **College of Business, Michigan Technological University** (Feb–May 2025). It serves as both a hands-on learning resource for R programming and a full NLP pipeline for lexicon-based sentiment analysis.

The notebook is structured in three parts — R fundamentals, basic data visualization, and an end-to-end sentiment analysis pipeline on real-world social media comment data.

---

## 📓 Notebook Structure

### Part 1 — R Basics
- Variables, data types, and arithmetic/logical operations
- Loading and exploring CSV datasets (`read.csv`, `head`, `tail`, `dim`, `summary`)
- Adding and deleting columns
- Business-context examples (e.g., chocolate sales dataset)

### Part 2 — Data Visualization
- Bar plots, histograms, scatter plots, line plots, box plots, pie charts
- Sales-by-country bar chart example using base R `barplot()`

### Part 3 — Sentiment Analysis Pipeline
A full NLP workflow applied first to a small sample dataset, then scaled to a **real-world social media comment dataset** (`sentiment2022data.csv`):

| Step | Function | Purpose |
|---|---|---|
| 1 | `unnest_tokens()` | Tokenize text into individual words |
| 2 | `anti_join(stop_words)` | Remove stop words (the, is, and...) |
| 3 | `inner_join(afinn_lexicon)` | Match words to AFINN sentiment scores |
| 4 | `group_by() + summarise()` | Aggregate scores per comment/id |
| 5 | `ifelse()` | Classify as Positive / Negative / Neutral |
| 6 | `write.csv()` | Export results for further analysis |

---

## 🧹 Data Cleaning (Real Dataset)

The real-world dataset required preprocessing before analysis:
- **Emoji removal** — custom `remove_emojis()` function using Unicode regex ranges
- **Foreign language removal** — `remove_non_english()` strips non-ASCII characters
- **Empty row removal** — filters rows left blank after cleaning using `filter(trimws(...))`

---

## 📊 Sentiment Classification

Using the **AFINN lexicon** — a word list where each word has a sentiment score from -5 (most negative) to +5 (most positive):

```
final_score > 0  →  Positive
final_score < 0  →  Negative
final_score = 0  →  Neutral
```

**Example output:**

| id | sentiment_words | final_score | sentiment |
|---|---|---|---|
| 1 | broke, worth | -4 | negative |
| 4 | amazing, exceeded | +6 | positive |
| 5 | fantastic, quick, perfectly | +7 | positive |

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | R |
| NLP Libraries | tidytext, tidyverse, dplyr |
| Sentiment Lexicon | AFINN |
| Environment | Jupyter Notebook (R kernel) |
| Data Formats | CSV |

---

## 📁 Repository Structure

```
sentiment-analysis-r/
├── R.ipynb                     # Main Jupyter Notebook (R kernel)
├── Data/
│   ├── Chocolate Sales.csv     # Sample dataset for R basics
│   ├── Afinn.csv               # AFINN sentiment lexicon
│   └── sentiment2022data.csv   # Real-world social media comments
├── images/                     # Notebook images (Anaconda, Jupyter setup)
└── README.md
```

---

## 🚀 How to Run

1. Install Anaconda: https://www.anaconda.com/products/distribution
2. Install the R kernel for Jupyter:
```r
install.packages('IRkernel')
IRkernel::installspec()
```
3. Install required packages (run once inside notebook):
```r
install.packages('tidyverse')
install.packages('tidytext')
```
4. Open `R.ipynb` in Jupyter Lab and run cells with `Shift + Enter`

---

## 🔮 Future Improvements

- [ ] Extend to additional lexicons (Bing, NRC) for comparison
- [ ] Add word cloud visualizations for positive/negative terms
- [ ] Build an interactive Shiny dashboard for sentiment exploration
- [ ] Apply to Twitter/Reddit data via API integration

---

## 👩‍💻 Author

**Vaishnavi Perka** — Research Assistant, College of Business, Michigan Tech  
[LinkedIn](https://www.linkedin.com/in/vaishnavi-perka) · [Portfolio](https://vaishnaviperka.github.io)
