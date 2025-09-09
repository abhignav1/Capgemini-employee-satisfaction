# Capgemini-employee-satisfaction
# Text Analysis on Capgemini Employee Satisfaction

## 📌 Project Overview
This project analyzes **26,411 employee reviews** from Capgemini (cleaned to **26,394**) to understand the key drivers of **work satisfaction** and **dissatisfaction**.  
We used **text mining (unigrams, bigrams, trigrams)**, **topic modeling (LDA)**, and **sentiment/emotion analysis (NRC)** to extract insights from the *Likes* and *Dislikes* sections of reviews, and combined them with structured fields such as ratings, career growth, and work-life balance.

**Business Question:**  
> What are the underlying factors influencing employee satisfaction and dissatisfaction at Capgemini, and how can these insights help improve retention, culture, and the overall employee experience?

---

## 🎯 Objectives
- Clean and preprocess raw employee reviews (normalize, remove noise, lemmatize).
- Identify the most common words, bigrams, and trigrams in Likes vs Dislikes.
- Build **correlation networks** of positive and negative terms.
- Use **LDA topic modeling** to find the dominant themes in reviews.
- Run **sentiment and emotion analysis** using the NRC lexicon.
- Link results to structured fields such as *Work Satisfaction* and *Overall Rating*.
- Provide actionable recommendations for HR and management.

---

## 🗃️ Dataset
- **Rows:** 26,411 (26,394 after cleaning)
- **Columns (13 original + 1 engineered):**  
  `Job_Title, Place, Department, Career_Growth, Work_Satisfaction, Salary_Benefits, Work_Life_Balance, Job_Security, Skill_Development, Management, Overall_Rating, Likes, Dislikes, review_text`  
- **review_text:** A merged column combining Likes and Dislikes for text analysis.
- **Granularity:** Employee-level review with both structured ratings and unstructured feedback.

---

## 🧹 Data Cleaning & Preprocessing
- Converted to lowercase.  
- Removed punctuation, numbers, HTML tags, and noise patterns (“naaa”, “ttt”).  
- Removed standard + custom stop words.  
- Combined `Likes` and `Dislikes` → `review_text`.  
- Lemmatized tokens to unify word forms (e.g., “working”, “worked” → “work”).

---

## 🔎 Exploratory Text Analysis
- **Likes:** Positive terms dominate higher ratings → “supportive”, “excellent”, “friendly”, “flexible”.  
- **Dislikes:** Salary, management, shifts, and resource allocation issues appear across all ratings.  
- **Bigrams:** Positive (“supportive team”, “learning opportunities”), Negative (“low salary hike”, “bench notice period”).  
- **Trigrams:** Positive (“supportive company culture”), Negative (“poor salary growth”, “night shift allowance”).

---

## 📊 Correlation Matrices
- **Dislikes:**  
  - `{pay, low, increment, hike}` = salary concerns cluster.  
  - `{bench, projects, notice, period}` = resource/assignment issues.  
  - `{politics, managers, organization, support}` = leadership & politics concerns.  
- **Likes:**  
  - `{development, projects, skills, training}` = growth.  
  - `{support, supportive, opportunity, organization}` = supportive culture.  
  - `{excellent, friendly, flexible}` = positive environment.

---

## 🧠 Topic Modeling (LDA)
- **Best k:** 2 (lowest perplexity).  
- **Topic 1 (Positive):** team, great, career, experience → teamwork & growth.  
- **Topic 2 (Negative):** hike, less, politics, appraisal → compensation & politics.  
- **Key Finding:** Even high-rated reviews still contain negative themes (especially salary/appraisal).

---

## 😊 Sentiment & Emotion Analysis (NRC)
- **Positive emotions:** joy, trust, anticipation → “friendly”, “career”, “opportunity”.  
- **Negative emotions:** anger, disgust, sadness → “politics”, “bad”, “pressure”.  
- **Dual words:** “salary” and “pay” show up in both positive and negative contexts → high emotional salience.  
- **Emotion vs satisfaction:** Negative emotions in *Dislikes* (sadness, fear, negative) correlate most strongly with lower satisfaction (≈ −0.12).

---

## 📌 Key Insights
1. **Culture & Team Support** are universal satisfaction drivers.  
2. **Compensation/Appraisal** concerns dominate dissatisfaction.  
3. **Bench/Staffing/Notice Period** frictions hurt morale and growth.  
4. **Shift/Transport Issues** (night shifts, cab support) affect well-being.  
5. Positive and negative experiences **co-exist in the same review** → star ratings can mask deeper issues.

---

## ✅ Recommendations
- **Salary & Promotion:** Transparent, predictable hike cycles; align with market.  
- **Bench & Allocation:** Reduce idle time via forecasting & skill-matching; review long notice periods.  
- **Manager Development:** Soft-skill training, mentoring, and career coaching.  
- **Culture & Learning:** Keep investing in supportive culture, growth, and flexible policies.  
- **Shift/Transport:** Improve night shift allowances and cab facilities.  
- **Continuous Feedback:** Regularly mine Dislikes for red flags; use emotion tracking as early warning.

---

## 🛠️ Tools & Technologies
- **Language:** R (primary).  
- **Key Packages:** `tidyverse`, `tidytext`, `textclean`, `tm`, `topicmodels`, `ldatuning`, `syuzhet`, `ggplot2`, `corrplot`, `wordcloud`.  
- **Optional Visuals:** `LDAvis`, `igraph`, `ggraph`.  
- **(Optional Python Alternative):** `pandas`, `scikit-learn`, `gensim`, `nltk`, `spacy`.

---

## 📂 Repository Structure

```mermaid
flowchart TD
  A[capgemini-text-analysis] --> B[data]
  A --> C[notebooks]
  A --> D[src]
  A --> E[reports]
  A --> F[README.md]
  A --> G[LICENSE]
  A --> H[.gitignore]

  B --> B1[sample]
  B --> B2[raw]

  C --> C1[capgemini_text_analysis.Rmd]

  D --> D1[cleaning.R]
  D --> D2[eda.R]
  D --> D3[topic_modeling.R]
  D --> D4[sentiment_analysis.R]

  E --> E1[figures]
  E --> E2[deck]
  E2 --> E21[Capgemini_Text_Analysis.pdf]
---
