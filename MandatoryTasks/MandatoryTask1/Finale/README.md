# Task D – Designing a Machine Learning System  
### WEC Intel SIG Submission by Macklin Chriss Miranda 241MN027

---

## Overview
This project is my solution for **Task D: Designing a Machine Learning System**, which builds upon the knowledge gained from **Task A, B, and C**.  

The objective is to **design and demonstrate a machine learning system** that can:
- Understand **questions in English**
- Extract the correct **answer from a given context**
- And finally, **translate that answer into another language (Hindi)**

This system, I integrated multiple NLP components into one pipeline.

---

## System Design

### 🔹 1. Components Used
- **Question Answering (QA) Model** – [`deepset/roberta-base-squad2`](https://huggingface.co/deepset/roberta-base-squad2)  
  - Was Trained on **SQuAD 2.0**, is capable of answering context-based English questions, including unanswerable ones.
  - I found this from Huggig face model hub

- **Translation Model** – [`Helsinki-NLP/opus-mt-en-hi`](https://huggingface.co/Helsinki-NLP/opus-mt-en-hi)  
  - Used for **English → Hindi** translation.
  - I found this in HF model hub as well. For French you can replace this model with `opus-mt-en-fr`. 

---

### 🔹 2. Architecture

            ┌──────────────────────────────┐
            │  English Question + Context  │
            └──────────────┬───────────────┘
                           │
                           ▼
                QA Model (RoBERTa-SQuAD2)
                           │
                  English Answer (Text)
                           │
                           ▼
              Translation Model (en → hi)
                           │
                           ▼
                    Hindi Answer Output

---

### 🔹 3. Summary of the Architecture
1. Take an English **question** and **context paragraph**.  
2. Use the QA model to **extract the answer** from the context.  
3. Feed the English answer to the translation model.  
4. Output the **translated answer** in Hindi.  

---

## Implementation

### Notebook File
> `Task_D_QuestionAnswering_and_Translation.ipynb`

This notebook contains:
- Step-by-step setup and explanations.
- Demonstrations with sample inputs and outputs.
- Function `get_hindi_answer(question, context)` that performs the entire workflow.

---

### 🔧 Requirements
To run the notebook, install:
```bash
pip install transformers torch sentencepiece
