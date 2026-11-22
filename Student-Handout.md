# CMP-262 — Assignment 11 Student Handout
## News Article Sentiment Analysis with TextBlob

**Purpose:** Learn to retrieve readable text from a public news webpage and compare two different ways of estimating sentiment. You do **not** need a textbook.

### 1. What is sentiment analysis?
Sentiment analysis is a method for estimating whether text expresses a positive, negative, or neutral attitude. It is not a reliable way to determine whether a news article is true, unbiased, or well written. News reports often contain quotes, factual descriptions, and mixed emotions, so the results require interpretation.

### 2. The tools you will use
- **requests** downloads the HTML from a webpage.
- **BeautifulSoup** helps you locate the article body and extract readable text.
- **TextBlob** divides text into sentences and provides sentiment scores.
- **PatternAnalyzer** is TextBlob's default sentiment analyzer.
- **NaiveBayesAnalyzer** predicts positive or negative sentiment using a classifier trained on movie reviews.
- **NLTK** supplies text-processing resources required by these tools.

### 3. A tiny practice example (not your assignment solution)
Run the following example to see what the default analyzer returns:

```python
from textblob import TextBlob

sample = TextBlob("The community enjoyed the new park.")
print(sample.sentiment)
```

You will see a sentiment result containing two values. **Polarity** ranges from -1 (negative) to +1 (positive); **subjectivity** ranges from 0 (objective) to 1 (subjective). A polarity near zero can mean neutral wording, but may also reflect mixed positive and negative language.

Try changing the sample sentence to see how the score changes. Do **not** use this practice sentence instead of a news article.

### 4. Understanding the second analyzer
The default TextBlob analyzer produces **polarity and subjectivity**. The Naive Bayes analyzer instead produces a **classification** (`pos` or `neg`) and two model probabilities, `p_pos` and `p_neg`. These probabilities represent the model's estimated probabilities for its two classes; they are **not** a measure of factual correctness or journalistic bias. Because the models work differently, they may disagree.

### 5. Choosing a news article
Select a **current** article with readable public HTML. Record the article's publisher, title, URL, publication date if shown, and the date you accessed it. Check the website's robots.txt and terms or scraping policy. Do not bypass restrictions, paywalls, logins, or anti-bot systems. If a source blocks access, select another.

**Tip:** Some sites render the article dynamically or include large amounts of navigation text. Pick an accessible source where you can identify the article body in the HTML.

### 6. From HTML to readable text
Webpages contain HTML tags such as `<p>` for paragraphs and `<article>` for an article section. BeautifulSoup parses the HTML so you can select the relevant elements. The expression `soup.get_text(strip=True)` removes HTML tags but extracts text from the **whole page** and can join words together. Prefer extracting the **article body** and preserving spaces with `get_text(" ", strip=True)` or joining paragraph text.

Inspect the extracted text before analyzing it. It should include the article, not menus, advertisements, cookie banners, or unrelated comments. Use a timeout when requesting a webpage and handle request failures appropriately.

### 7. Analyzing the full article and its sentences
First analyze the **whole article** using the default TextBlob analyzer, then loop through **every sentence** and display its sentiment. Repeat using NaiveBayesAnalyzer with the **same article text** and the same sentence boundaries. Label your printed outputs so a reader can tell which analyzer produced each result.

A very long article may contain many sentences. You still need to report the results for each sentence. You can format output neatly, but do not silently omit sentences.

### 8. Comparing results thoughtfully
Your comparison should use **actual values** from your notebook, not invented scores. Explain whether the overall conclusions agree, include one specific sentence-level example, and discuss why the analyzers may disagree. Remember that polarity and Naive Bayes probabilities are **different kinds of numbers** and should not be compared as if they share the same scale.

**Questions to consider:** Did a quotation change the tone? Did one method seem more confident? Could extra webpage text have influenced the scores? Does training on movie reviews limit the Naive Bayes model for news?

### 9. Setup and common issues
Install the listed dependencies using `python -m pip install -r requirements.txt` in the VS Code terminal. Select that same Python environment as your Jupyter kernel.

If you see a missing NLTK resource error, run the appropriate download once:

```python
import nltk
nltk.download("movie_reviews")
nltk.download("punkt")
nltk.download("punkt_tab")
```

- **ModuleNotFoundError:** Check that you installed packages in the environment selected by your notebook.
- **HTTP 403 or 429:** Do not bypass the site's restrictions; choose a different article or wait as permitted.
- **Empty article text:** Recheck the HTML selectors; some webpages load text with JavaScript.
- **Missing tokenizer resource:** Download the named NLTK data package.
- **Sentiment looks strange:** Inspect the extracted text and remember that sentiment analysis is imperfect.

### 10. What to submit
Complete `NewsArticleSentimentAnalysis.ipynb` with commented Python, Markdown explanations, visible program output, and a written comparison. Complete `AI-Use-Report.md`. Keep the starter files and README. Restart your notebook kernel, choose **Run All**, save the outputs, and submit the link to **your own public GitHub repository** in Blackboard Ultra.

**Total: 100 points.** See `RUBRIC.md` for the breakdown.

### Final checklist
- [ ] Current article, publisher, headline, URL, and dates documented
- [ ] Responsible webpage retrieval and readable article-only text
- [ ] Whole-article and every-sentence default TextBlob sentiment
- [ ] Whole-article and every-sentence Naive Bayes sentiment
- [ ] Real scores compared, with a sentence example and limitation
- [ ] Notebook runs and outputs are saved
- [ ] AI-use report completed and GitHub repository link submitted
