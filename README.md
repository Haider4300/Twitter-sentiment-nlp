# Author: Ali Haider (AI-Engineer)
# NLP Engineering

A Natural Language Processing project focused on Twitter sentiment analysis, built with Python and NLTK.

## Project Overview

This project provides tools for processing and analyzing Twitter data, including tweet preprocessing, tokenization, stemming, and frequency analysis for sentiment classification tasks.

## Tech Stack

- **Python**: >=3.11.14
- **Package Manager**: uv

## Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `nltk` | >=3.9.4 | Natural language processing (tokenization, stemming, stopwords) |
| `pandas` | >=3.0.1 | Data manipulation and analysis |
| `matplotlib` | >=3.10.8 | Data visualization |
| `ipykernel` | >=7.2.0 | Jupyter notebook support |

## Project Structure

```
nlp-engineering/
├── Labs/
│   ├── __init__.py      # Package initializer
│   └── utils.py         # NLP utility functions
├── main.py              # Entry point
├── pyproject.toml       # Project configuration
└── README.md            # Documentation
```

## Modules

### Labs/utils.py

Contains core NLP processing functions:

#### `process_tweet(tweet)`
Processes a raw tweet string into cleaned, stemmed tokens.

**Input:** `tweet` (str) - Raw tweet text
**Output:** List of processed words

**Processing steps:**
1. Removes stock market tickers (e.g., `$GE`)
2. Removes "RT" retweet markers
3. Removes hyperlinks
4. Removes hashtag symbols (keeps the word)
5. Tokenizes using TweetTokenizer (lowercase, handles Twitter-specific patterns)
6. Removes English stopwords and punctuation
7. Applies Porter stemming

#### `build_freqs(tweets, ys)`
Builds a frequency dictionary mapping (word, sentiment) pairs to their counts.

**Input:**
- `tweets`: List of tweet strings
- `ys`: Array of sentiment labels (0=negative, 1=positive)

**Output:** Dictionary mapping `(word, sentiment)` tuples to frequency counts

**Use case:** Training data preparation for sentiment classification models (e.g., logistic regression, Naive Bayes).

## Installation

```bash
# Install uv if not already installed
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install dependencies
uv sync
```

## Usage

```python
from Labs.utils import process_tweet, build_freqs

# Process a single tweet
tweet = "RT @user: Loving this product! $STOCK #review https://example.com"
tokens = process_tweet(tweet)
# Output: ['love', 'product']

# Build frequency dictionary for training data
tweets = ["Great product!", "Terrible experience."]
labels = [1, 0]  # 1=positive, 0=negative
freqs = build_freqs(tweets, labels)
```

## Development

```bash
# Activate virtual environment
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Run the main entry point
python main.py
```

