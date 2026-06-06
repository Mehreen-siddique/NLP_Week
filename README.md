# NLP_Week
# Roman Urdu Sentiment Analysis using Fine-Tuned XLM-RoBERTa

## Overview

This project presents a **Roman Urdu Sentiment Analysis System** built using a fine-tuned **XLM-RoBERTa (Cross-Lingual RoBERTa)** transformer model. The system classifies Roman Urdu text into three sentiment categories:

* Positive
* Negative
* Neutral

The project demonstrates the complete Natural Language Processing (NLP) pipeline, including data preprocessing, model evaluation, fine-tuning, and deployment using Streamlit and Hugging Face Spaces.

---

## Problem Statement

Roman Urdu is widely used on social media platforms, messaging applications, online reviews, and discussion forums. Unlike standard Urdu script, Roman Urdu is written using English alphabets and lacks standardized spelling conventions.

Examples:

| Roman Urdu Text           | Sentiment |
| ------------------------- | --------- |
| bohat acha tha yeh        | Positive  |
| bilkul bekar hai          | Negative  |
| theek tha lekin khas nahi | Neutral   |

Due to spelling variations and the scarcity of annotated datasets, sentiment analysis for Roman Urdu remains a challenging NLP task.

---

## Dataset Description

The dataset consists of approximately **19,664 Roman Urdu sentences** annotated with sentiment labels.

### Dataset Columns

| Column       | Description                                   |
| ------------ | --------------------------------------------- |
| sentences    | Original Roman Urdu sentence                  |
| Review       | Sentiment label (Positive, Negative, Neutral) |
| sentiment    | Empty / NaN column                            |
| cleaned_text | Preprocessed text used for training           |

### Example

| sentences          | Review   |
| ------------------ | -------- |
| bohat acha tha yeh | Positive |
| mujhe pasand aya   | Positive |
| bilkul bekar hai   | Negative |
| theek tha          | Neutral  |

---

## Data Preprocessing

Several preprocessing steps were applied before model training:

### 1. Lowercasing

Convert text to lowercase.

Example:

```text
Bohat Acha Tha Yeh
↓
bohat acha tha yeh
```

### 2. Removing Extra Spaces

```text
bohat   acha   tha
↓
bohat acha tha
```

### 3. Removing Special Characters

```text
acha!!! movie thi :)
↓
acha movie thi
```

### 4. Handling Missing Values

Rows containing missing text were removed.

---

## Models Evaluated

Several multilingual sentiment models were evaluated before selecting the final model.

### 1. Multilingual BERT

Model:

```python
nlptown/bert-base-multilingual-uncased-sentiment
```

Accuracy Achieved:

```text
35%
```

---

### 2. Twitter XLM-R Sentiment Model

Model:

```python
cardiffnlp/twitter-xlm-roberta-base-sentiment
```

Accuracy Achieved:

```text
45%
```

---

### 3. Fine-Tuned XLM-RoBERTa (Final Model)

Model:

```python
xlm-roberta-base
```

Accuracy Achieved:

```text
65%
```

This model provided the best performance and was selected for deployment.

---

## Why XLM-RoBERTa?

XLM-RoBERTa is a multilingual transformer trained on 100+ languages.

Advantages:

* Strong multilingual understanding
* Handles code-mixed language effectively
* Robust contextual embeddings
* State-of-the-art performance on low-resource languages

---

## Model Training

### Train-Test Split

```python
train_test_split(
    test_size=0.2,
    stratify=labels,
    random_state=42
)
```

Dataset Split:

| Split    | Percentage |
| -------- | ---------- |
| Training | 80%        |
| Testing  | 20%        |

---

### Hyperparameters

```python
learning_rate = 2e-5
batch_size = 8
epochs = 3
max_length = 128
weight_decay = 0.01
```

---

## Evaluation Metrics

The model was evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* Classification Report

### Final Accuracy

```text
65%
```

---

## Project Structure

```text
RomanUrduSentimentAnalysis/
│
├── app.py
├── requirements.txt
├── README.md
│
├── notebooks/
│   └── training.ipynb
│
├── dataset/
│   └── roman_urdu_dataset.csv
│
├── roman_urdu_sentiment_model/
│   ├── config.json
│   ├── tokenizer.json
│   ├── tokenizer_config.json
│   ├── model.safetensors
│   └── training_args.bin
│
└── outputs/
    └── evaluation_results
```

---

## Streamlit Application

The trained model is integrated into a Streamlit application.

### Features

* Real-time sentiment prediction
* Roman Urdu text input
* Confidence score display
* Positive, Neutral, and Negative classification
* User-friendly interface

Example:

Input:

```text
bohat acha tha yeh
```

Output:

```text
Sentiment: POSITIVE
Confidence: 91%
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/roman-urdu-sentiment-analysis.git
```

Move into the project directory:

```bash
cd roman-urdu-sentiment-analysis
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Run Locally

```bash
streamlit run app.py
```

Open:

```text
http://localhost:8501
```

---

## Deployment

The application is deployed using:

* Hugging Face Spaces
* Streamlit
* Transformers
* PyTorch

---

## Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Scikit-learn
* Transformers
* Datasets
* PyTorch
* Streamlit

### Platform

* Kaggle
* Hugging Face Spaces
* GitHub

---

## Challenges Faced

* Non-standard Roman Urdu spellings
* Limited Roman Urdu sentiment resources
* Class imbalance
* Multilingual sentiment transfer limitations
* Large transformer model deployment

---

## Future Improvements

* Increase dataset size
* Apply data augmentation
* Hyperparameter optimization
* Domain-specific fine-tuning
* Improve neutral sentiment detection
* Deploy REST API using FastAPI
* Add sentiment visualization dashboards

---

## Results Summary

| Model                   | Accuracy |
| ----------------------- | -------- |
| Multilingual BERT       | 35%      |
| Twitter XLM-R Sentiment | 45%      |
| Fine-Tuned XLM-RoBERTa  | 65%      |

The fine-tuned XLM-RoBERTa model significantly outperformed the baseline multilingual sentiment models and demonstrated effective sentiment classification for Roman Urdu text.

---

## Author

**Mehreen siddique**

Roman Urdu Sentiment Analysis Project

Built using Transformer-based Deep Learning and Multilingual NLP techniques.

https://huggingface.co/spaces/Mehreen44/Roman_Urdu_app

