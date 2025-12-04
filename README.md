# MSDS25062_IRTM_HW03
# Information Retrieval System

A simple Python-based information retrieval system that implements TF-IDF (Term Frequency-Inverse Document Frequency) scoring to search and rank documents based on query relevance.

## Overview

This project consists of two main components:
- **read_data.py**: Loads and processes text documents from a dataset
- **ir_system.py**: Implements search functionality using TF-IDF weighting and cosine similarity

## Features

- Document preprocessing (tokenization, stopword removal, stemming)
- TF-IDF vectorization for documents and queries
- Cosine similarity-based ranking
- Support for multi-term queries
- Efficient document retrieval and scoring

## Requirements

```
numpy
nltk
```

## Setup

1. Install required packages:
```bash
pip install numpy nltk
```

2. Download NLTK data:
```python
import nltk
nltk.download('stopwords')
nltk.download('punkt')
```

## Usage

### Loading Documents

```python
from read_data import read_documents

# Load documents from your dataset
documents = read_documents('path/to/your/dataset')
```

### Searching Documents

```python
from ir_system import IRSystem

# Initialize the IR system
ir_system = IRSystem(documents)

# Build the index
ir_system.build_index()

# Search for documents
query = "your search query"
results = ir_system.search(query, top_k=10)

# Display results
for doc_id, score in results:
    print(f"Document {doc_id}: Score = {score:.4f}")
```

## Complete Example

```python
from read_data import read_documents
from ir_system import IRSystem

# Load your documents
docs = read_documents('data/documents.txt')

# Create and build IR system
ir = IRSystem(docs)
ir.build_index()

# Search
results = ir.search("information retrieval", top_k=5)

# Show results
for doc_id, score in results:
    print(f"Doc {doc_id}: {score:.4f}")
```

## How It Works

1. **Preprocessing**: Text is tokenized, converted to lowercase, stopwords are removed, and words are stemmed
2. **Indexing**: Documents are converted into TF-IDF vectors
3. **Query Processing**: Search queries undergo the same preprocessing
4. **Ranking**: Documents are ranked using cosine similarity between query and document vectors
5. **Results**: Top-k most relevant documents are returned with their similarity scores

## Components

### read_data.py
- `read_documents()`: Loads documents from the specified data source
- Handles document parsing and initial formatting

### ir_system.py
- `IRSystem`: Main class for the information retrieval system
  - `build_index()`: Creates TF-IDF index from documents
  - `search()`: Processes queries and returns ranked results
  - `preprocess()`: Handles text preprocessing
  - `compute_tfidf()`: Calculates TF-IDF weights
  - `cosine_similarity()`: Computes similarity scores

## Technical Details

- Uses Porter Stemmer for word stemming
- English stopwords from NLTK are removed by default
- TF-IDF weights computed using standard formulas
- Cosine similarity used as the ranking metric



## Author

Afzaal Kareem
msds25062@itu.edu.pk
