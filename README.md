# IMDB Sentiment Analysis

[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.32-red?logo=streamlit)](https://streamlit.io)
[![Docker](https://img.shields.io/badge/Docker-Containerised-blue?logo=docker)](https://docker.com)
[![Heroku](https://img.shields.io/badge/Heroku-Deployed-purple?logo=heroku)](https://heroku.com)
[![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-green?logo=github-actions)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

> NLP project that classifies movie review sentiment (positive/negative) using two approaches. a classical ML pipeline with scikit-learn, and zero-shot clasification with the OpenAI API.

---

## Project Structure
imdb_sentiment/
├── data/
│   └── IMDB Dataset.csv
│
├── models/
│   ├── sentiment_pipeline.joblib
│   └── label_encoder.joblib
│
├── src/
│   ├── get_data.py
│   ├── preprocessing.py
│   ├── train.py
│   └── api.py
│
└── SentimentOpenAI.ipynb

## Aproaches
1. Classical ML Pipeline
   - Text preprocessing
   - Features
   - Classifier
   - Served via FastAPI
  
2. OpenAI Zero-Shot (SentimentOpenAI.ipynb)
   - Prompts `gpt-4o-mini` to classify each review as `positive`or `negative`
   - Achievec **90% accuracy** on a 10-sample test

## Setup

`python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt`

For the OenAI notebook, create a `.env` file

`OPENAI_API_KEY=your_key_here`


## Usage
### Download Data
`python src/get_data.py`

### Train the model
`python src/train.py`

Saves `models/sentiment_pipeline.joblib` and `models/label_encoder.joblib`.

### Run the API
'uvicorn src.api:app --reload`

### Endpoints
  - `GET /` - health check
  - `POST /predict` - classify a review


`curl -X POST http://localhost:8000/predict \
  -H "Content-Type: application/json" \
  -d '{"review": "This movie was absolutely fantastic!"}'`



  `{"sentiment": "positive", "probability": 0.93}`

  ## Dataset
  










