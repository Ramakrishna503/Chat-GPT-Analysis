# ChatGPT User Reviews: Exploratory Data Analysis & NLP Sentiment Pipeline

An end-to-end data analysis and Natural Language Processing (NLP) project exploring **196,727 user reviews** of the ChatGPT mobile application. This repository contains a Google Colab / Jupyter Notebook that cleans raw text data, evaluates user rating trends, computes sentiment polarity and subjectivity scores, and extracts key positive and critical themes.

---

## 📊 Key Findings & Metrics

* **Dataset Volume:** Analyzed **193,154 unique reviews** (after removing 3,573 duplicate `review_id` records and handling 6 missing review entries).
* **Overall User Satisfaction:** High average star rating of **4.51 / 5.00** (median: 5.00), with an average review length of **8.69 words**.
* **NLP Sentiment Breakdown (TextBlob Polarity):**
  * **Positive (`> 0.05`):** 146,360 reviews (**75.77%**)
  * **Neutral (`-0.05` to `0.05`):** 39,764 reviews (**20.59%**)
  * **Negative (`< -0.05`):** 7,030 reviews (**3.64%**)
* **Rating vs. Polarity Alignment:** Mean NLP polarity scales consistently with user star ratings—from **0.013** for 1-star reviews up to **0.500** for 5-star reviews.
* **Key Themes:**
  * **Positive Drivers (4–5 Stars):** Users frequently praise utility and performance using terms like *good*, *best*, *nice*, *great*, *helpful*, *amazing*, *useful*, and *excellent*.
  * **Critical Pain Points (1–2 Stars):** Negative reviews center around technical friction and accuracy issues, highlighted by keywords such as *working*, *error*, *login*, *answer*, *wrong*, *phone*, and *google*.

---

## 🛠️ Tech Stack & Libraries

* **Data Manipulation:** `pandas`, `numpy`
* **NLP & Text Processing:** `textblob`, `nltk` (stopwords), `re` (regular expressions), `collections.Counter`
* **Data Visualization:** `matplotlib`, `seaborn`, `wordcloud`
* **Environment:** Google Colab / Jupyter Notebook (Python 3)

---

## 📂 Project Workflow

1. **Data Loading & Inspection**
   * Loaded `chatgpt_reviews.csv` (`196,727 rows × 4 columns`: `Review Id`, `Review`, `Ratings`, `Review Date`).
2. **Data Preparation & Cleaning**
   * Standardized column headers to `snake_case`.
   * Deduplicated records based on `review_id` (removed 3,573 duplicates).
   * Imputed missing review text with empty strings and enforced `numeric` and `datetime` data types.
   * Engineered `year_month` and `word_count` features for temporal and structural EDA.
3. **Exploratory Data Analysis (EDA)**
   * Visualized the distribution of user star ratings (1–5) and monthly review volume trends over time.
   * Computed descriptive statistics across ratings and word counts.
4. **Sentiment Analysis**
   * Applied `TextBlob` across all 193,154 cleaned reviews to extract **Polarity** (`-1.0` to `+1.0`) and **Subjectivity** (`0.0` to `1.0`).
   * Classified reviews into `Positive`, `Neutral`, and `Negative` buckets and cross-tabulated mean/median NLP scores against star ratings.
5. **Keyword Extraction & Visualization**
   * Filtered standard English stopwords alongside domain-specific filler terms (`app`, `chatgpt`, `ai`, `gpt`, `chat`, etc.).
   * Extracted the top 15 most frequent keywords for both positive (4–5 stars) and critical (1–2 stars) segments.
   * Generated a 4-panel summary dashboard (Sentiment Distribution, Polarity by Star Rating Boxplot, Subjectivity KDE Histogram, and Top Positive Keywords) along with a high-resolution Word Cloud.

---

## 🚀 How to Run

1. **Clone or Download** the `.ipynb` notebook file.
2. **Prepare the Dataset:** Place `chatgpt_reviews.csv` in your Google Drive at `/content/drive/MyDrive/Data/chatgpt_reviews.csv` (or update the `file_path` variable in Cell 4 to match your local directory).
3. **Install Dependencies** (if running locally outside Google Colab):
   ```bash
   pip install pandas numpy matplotlib seaborn textblob wordcloud nltk
