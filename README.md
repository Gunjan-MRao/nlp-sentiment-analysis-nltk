Sentiment Analysis on Student Reviews (NLTK + Weighted Lexicon)
Classify student-written reviews into Positive / Neutral / Negative using classic NLP preprocessing and a transparent weighted lexicon scoring approach.

Why this project
This project is a lightweight, interpretable baseline for sentiment analysis that demonstrates an end-to-end text analytics workflow: data setup → preprocessing → scoring → labelling → summary insights. It’s designed to be easy to audit (you can see exactly why a review was labelled positive or negative).

What it does
Given a small set of student review texts, the notebook:

Cleans and preprocesses text (tokenisation, lowercasing, stopword removal, stemming).

Scores each review using a weighted positive/negative lexicon.

Assigns a sentiment label based on the net score:

Positive if total score > 0

Negative if total score < 0

Neutral if total score = 0

Produces a per-review output table with positive score, negative score, total score, and label.

Summarises the sentiment distribution across the dataset.

Dataset
For demonstration, the notebook uses 6 student review text samples embedded directly in the notebook.

If you want to reuse the pipeline on your own data, replace the reviews = [...] list with your own text list (or load from a CSV) and re-run the notebook.

Method (high level)
Preprocess

Tokenise review text

Remove non-alphabetic tokens

Remove English stopwords

Apply Porter stemming

Score

Stem the lexicon to align with stemmed tokens

Compute:

pos_score = sum of positive token weights

neg_score = sum of negative token weights

total_score = pos_score - neg_score

Classify

Map total_score to Positive / Negative / Neutral

Summarise

Produce a label count and percentage breakdown

Results (from the included sample)
Reviews analysed: 6

Sentiment split:

Positive: 4 (66.7%)

Negative: 2 (33.3%)

Neutral: 0

The notebook also outputs a per-review table including pos_score, neg_score, total_score, and the assigned label.

Repository structure
notebooks/

sentiment_nltk_weighted_lexicon.ipynb — main analysis notebook

requirements.txt — Python dependencies (recommended)

How to run
1) Create and activate an environment
Example (conda):

conda create -n sentiment-nltk python=3.10 -y

conda activate sentiment-nltk

2) Install dependencies
pip install -r requirements.txt

3) Run the notebook
Open and run:

notebooks/sentiment_nltk_weighted_lexicon.ipynb

The notebook downloads required NLTK resources (punkt, stopwords) automatically on first run.

Notes on evaluation and limitations
This is a rule-based baseline (lexicon scoring), not a supervised ML classifier trained on labelled data. That makes it easy to interpret, but it can struggle with:

Negation (e.g., “not good”)

Sarcasm/irony

Domain-specific language not present in the lexicon

Sensitivity to the chosen weights and vocabulary

Possible next improvements
Add a labelled dataset and evaluate with accuracy/F1/confusion matrix.

Expand the lexicon or use a standard sentiment lexicon (and compare results).

Handle negation (e.g., “not” scopes) and intensifiers (“very”, “extremely”).

Replace the baseline with a supervised model (e.g., logistic regression, linear SVM) using TF-IDF features.

Coursework note
This work was completed as part of Coventry University coursework and is shared here as a learning + portfolio project.
