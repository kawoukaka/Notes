# Tokenization and Normalization

## Glossary
- Tokenization: split text into tokens. https://en.wikipedia.org/wiki/Lexical_analysis
- Normalization: canonicalize text (case-folding, Unicode). https://en.wikipedia.org/wiki/Unicode_equivalence
- Stemming/Lemmatization: reduce words to root forms. https://en.wikipedia.org/wiki/Stemming

## Usage (Specific)
- Search indexing pipelines (normalize accents, case, punctuation).
- Log analysis with structured fields extracted from raw text.
- Feature extraction for ML models (bag-of-words, n-grams).

## Average Time Complexity
- Average: O(n) over input length with linear scanning and regex/tokenizer rules.

## Real-World Example
- Lucene Analyzer framework. https://github.com/apache/lucene

## Tradeoffs and Failure Modes
- Over-normalization can collapse distinct tokens and harm relevance.
- Locale-specific rules can change behavior (Turkish I).

## LeetCode
- 125 Valid Palindrome
- 49 Group Anagrams

## Python Implementation
```python
import re
import unicodedata

def normalize_text(text):
    text = unicodedata.normalize("NFKC", text)
    text = text.casefold()
    return text


def tokenize(text):
    text = normalize_text(text)
    return re.findall(r"[a-z0-9]+", text)
```
