# CMP-262 — Assignment 11: News Article Sentiment Analysis

**Instructor: Prof. Amjed Hedhli | Total: 100 points | Due: See Blackboard Ultra**

## Objective

Retrieve a current news article using Python's **requests** and **BeautifulSoup**, then use **TextBlob** to compare two approaches to sentiment analysis on the full article **and on every sentence**.

## Student Handout

Read [Student-Handout.md](Student-Handout.md) for a beginner-friendly explanation of the tools, sentiment scores, setup, troubleshooting, and submission checklist. No textbook is required.

## Getting Started

1. Select **Use this template → Create a new repository** (when enabled); otherwise fork the starter repository.
2. Create a **public** repository under your own GitHub account. Suggested name: `LastName-FirstName-CMP262-Assignment11`.
3. Clone your own repository and open the entire folder in **Visual Studio Code**.
4. Open `NewsArticleSentimentAnalysis.ipynb`, select your Python kernel, and complete all TODOs.
5. Complete `AI-Use-Report.md`.
6. Save the notebook **with outputs** and submit your own repository link in Blackboard Ultra.

## Setup

If the imports fail, install packages into the Python environment selected for your notebook:

```bash
python -m pip install -r requirements.txt
```

The Naive Bayes analyzer also requires NLTK resources. Download them once as needed:

```python
import nltk
nltk.download("movie_reviews")
nltk.download("punkt")
nltk.download("punkt_tab")
```

## Directions

### Part 1 — Part 1: Sentiment of a News Article

- Choose a **current news article**. Record the publisher, headline, URL, publication date (if provided), and access date.
- Use `requests` and `BeautifulSoup` to retrieve the webpage and extract article text.
- For example, `text = soup.get_text(strip=True)` for removing HTML tags. For a real news page, target the article body and preserve word spacing; `get_text(" ", strip=True)` can help.
- Construct a standard `TextBlob` from the article's text.
- Display sentiment **for the entire article** and **for each sentence**, showing polarity and subjectivity.

### Part 2 — Part 2: NaiveBayesAnalyzer

- Repeat the analysis with `TextBlob(article_text, analyzer=NaiveBayesAnalyzer())`.
- Display the sentiment classification (`pos` or `neg`) and the positive and negative probabilities for the **full article** and **each sentence**.
- Analyze the **same article text** with both methods so you can compare them.

### Part 3 — Interpretation and submission

- Write a paragraph explaining the differences in the two analyses, citing real scores and **at least one sentence-level example**.
- Explain one potential reason for disagreement and one limitation.
- Use Markdown cells to organize your notebook and comment on important Python steps.
- Restart the kernel, **Run All**, and save the notebook with successful outputs.
- Complete `AI-Use-Report.md`.

**Responsible scraping:** Read the site's robots.txt and applicable policies. Do not bypass paywalls, logins, rate limits, or anti-bot systems. If your selected source prohibits automated access, choose another news article. Do not scrape personal data.

## Grading Rubric — 100 points

See [RUBRIC.md](RUBRIC.md) for the full 100-point grading breakdown.

## Repository Files

```text
CMP262-Assignment-11/
├── .github/
│   └── copilot-instructions.md
├── .vscode/
│   ├── extensions.json
│   └── settings.json
├── data/
│   └── .gitkeep
├── NewsArticleSentimentAnalysis.ipynb
├── README.md
├── Student-Handout.md
├── RUBRIC.md
├── AI-Use-Report.md
├── requirements.txt
└── .gitignore
```

The `data/` folder is provided for optional processing artifacts. A CSV file is **not required** for this assignment. Do not redistribute full copyrighted article text unnecessarily.

## Saving and Submitting

```bash
git status
git add .
git commit -m "Complete Assignment 11 sentiment analysis"
git push
```

Open your GitHub repository to confirm that the notebook displays your code and outputs. **Submit your public repository URL in Blackboard Ultra**. GitHub upload alone does not count as a Blackboard submission.

AI may help explain concepts or debugging; students must perform and understand the submitted analysis, and document AI use in `AI-Use-Report.md`.
