# Nutrition RAG Question Answering System

## Overview
This project implements an end-to-end Retrieval-Augmented Generation (RAG) system for answering factual questions in the domain of human nutrition. The system uses an open-source nutrition textbook as its knowledge source and combines semantic retrieval with a language model to generate context-based answers.

## Pipeline

### 1. Document Processing and Embedding Creation
- Load and extract text from a PDF textbook (*Human Nutrition: 2020 Edition*)
- Clean and preprocess the text
- Split text into sentences and group them into fixed-size chunks
- Convert each chunk into embeddings using **all-mpnet-base-v2**

### 2. Retrieval and Answer Generation
- Convert queries into embeddings
- Retrieve relevant chunks using similarity search
- Construct a prompt using retrieved context and query
- Generate answers using a language model (**Gemma 7B**)

## Models Used

**Embedding Model:**
- `sentence-transformers/all-mpnet-base-v2`

**Language Model:**
- `google/gemma-7b-it`  
- TinyLlama (fallback if GPU is unavailable)

## Dataset

**Source:**
- *Human Nutrition: 2020 Edition*  
- https://pressbooks.oer.hawaii.edu/humannutrition2/

**Test Set:**
- 40 manually annotated question–answer pairs

**Training Set:**
- Small subset used for experimentation (no fine-tuning)

## Results

- **Exact Match (EM):** 0.48  
- **F1 Score:** 0.57  
- **Recall:** 0.63  

These results indicate that the system retrieves relevant information effectively, though some answers are partially incomplete or contain extra text.

## How to Run

1. Open the notebook:
   Assignment_2_RAG.ipynb

2. Run all cells in order.

3. Output file will be generated at:
   system_outputs/system_output_1.txt
   
## Project Structure
├── data/
│ ├── test/
│ │ ├── questions.txt
│ │ ├── reference_answers.txt
│ ├── train/
│ ├── questions.txt
│ ├── reference_answers.txt
├── system_outputs/
│ └── system_output_1.txt
├── Assignment_2_RAG.ipynb
├── README.md

## Summary

This project demonstrates a complete RAG pipeline that uses external knowledge for retrieval and generates concise, context-based answers using a language model.
