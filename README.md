# LSTM Next-Word Prediction

An NLP project that uses a Long Short-Term Memory (LSTM) neural network to predict the next word in a text sequence. The project combines TensorFlow/Keras for deep learning with Streamlit for an interactive web application.

## Overview

Next-word prediction is a Natural Language Processing (NLP) task in which a model learns patterns from text and predicts a likely word given a sequence of preceding words.

In this project, the model is trained on Shakespeare's *Hamlet* text. The text is tokenized into numerical sequences, and the model learns to predict the next word from previous words. The trained model and tokenizer are saved and reused by a Streamlit application.

For example:

**Input:** `To be or not to be`

**Possible prediction:** `that`

The prediction depends on the patterns learned during training; the model is not guaranteed to reproduce the original text exactly.

## Features

- Text preprocessing and word tokenization.
- N-gram sequence generation for next-word prediction.
- Padding sequences to a consistent length.
- LSTM-based neural network for sequence learning.
- Softmax output layer for predicting the next word from the vocabulary.
- Saved model and tokenizer for reuse without retraining.
- Interactive Streamlit web interface.
- Model inference using user-provided text.

## Technology Stack

- **Python** — core programming language.
- **TensorFlow / Keras** — neural network development and training.
- **NumPy** — numerical operations and array processing.
- **NLTK** — access to Shakespeare's Hamlet text corpus.
- **Scikit-learn** — splitting data into training and testing sets.
- **Streamlit** — interactive web application.
- **Pickle** — saving and loading the tokenizer.
- **Jupyter Notebook / Google Colab** — experimentation and model training.

## How It Works

### 1. Data Collection

The project uses Shakespeare's *Hamlet* text as its training corpus.

### 2. Text Preprocessing

A Keras tokenizer builds a vocabulary and converts words into integer IDs. This allows the neural network to process text numerically.

### 3. N-gram Sequence Generation

The text is converted into progressively longer sequences. For example:

- `To be`
- `To be or`
- `To be or not`
- `To be or not to`

Each sequence uses its final word as the target, while the preceding words are used as input.

### 4. Padding and Dataset Preparation

Sequences are padded to a consistent length so they can be processed in batches. The input sequences and their next-word targets are separated into training and testing sets.

### 5. Model Architecture

The neural network uses the following layers:

1. **Embedding Layer** — converts word IDs into dense vector representations.
2. **LSTM Layer** — learns sequential relationships and contextual patterns in the input.
3. **Dropout Layer** — helps reduce overfitting during training.
4. **Dense Layer with Softmax** — produces a probability distribution over the vocabulary for next-word prediction.

The model is trained using categorical cross-entropy loss and the Adam optimizer.

### 6. Model and Tokenizer Saving

The trained model is saved as `next_word_prediction.keras`, and the fitted tokenizer is saved as `tokenizer.pickle`. Saving both allows the application to reuse the learned weights and the original word-to-ID mappings.

### 7. Prediction and Deployment

The Streamlit application accepts text from a user, converts it into token IDs, pads it to the expected input length, and passes it to the trained model. The model selects the word with the highest predicted probability and displays it as the next-word prediction.

## Project Structure

```text
lstm implementation final/
├── app.py
├── lstm_rnn_implementation.ipynb
├── hamlet.txt
├── next_word_prediction.keras
├── tokenizer.pickle
├── requirements.txt
├── .gitignore
└── README.md
```

## Installation and Setup

### Prerequisites

- Python 3.10 or another Python version compatible with the project's dependencies.
- pip.
- Git.
- A terminal or command prompt.

### 1. Clone the Repository

```bash
git clone <https://github.com/himanshu22ye/Lstm-rnn-implementation.git>
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it on Linux or WSL:

```bash
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Streamlit Application

```bash
streamlit run app.py
```

Open the local URL printed by Streamlit, usually `http://localhost:8501`.

## Saved Artifacts

| File | Purpose |
|---|---|
| `next_word_prediction.keras` | Trained LSTM model and learned weights |
| `tokenizer.pickle` | Fitted tokenizer and vocabulary mappings |
| `hamlet.txt` | Training text corpus |
| `lstm_rnn_implementation.ipynb` | Notebook containing the training workflow |
| `app.py` | Streamlit application |
| `requirements.txt` | Python dependency list |

## Limitations

- Prediction quality depends on the training data, preprocessing, and model performance.
- The model may predict a different word from the original Shakespeare text.
- A limited training corpus restricts the model's vocabulary and ability to generalize.
- The model predicts one next word at a time rather than generating a complete passage.
- Words outside the tokenizer's vocabulary may not be handled as expected.

## Future Improvements

- Train on a larger and more diverse text corpus.
- Improve preprocessing and evaluate alternative sequence lengths.
- Tune hyperparameters to improve validation performance.
- Compare LSTM results with a simple RNN and GRU.
- Extend the application to generate multiple words iteratively.
- Deploy the application to a hosted platform.

## Learning Outcomes

This project demonstrates practical experience with NLP preprocessing, tokenization, n-gram generation, sequence padding, LSTM neural networks, model evaluation, artifact persistence, and Streamlit deployment.

## Disclaimer

This project is intended for educational purposes and demonstrates a basic neural next-word prediction pipeline. Predictions are generated from learned statistical patterns and are not guaranteed to be grammatically or contextually correct.

