# 🚀 ArXiv Paper Intelligence System (RAG Pipeline)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-orange)
![FAISS](https://img.shields.io/badge/Meta-FAISS-blue)
![Gradio](https://img.shields.io/badge/UI-Gradio-lightgrey)

An advanced, end-to-end Natural Language Processing (NLP) application built to semantically search, analyze, and summarize scientific literature. Utilizing a Retrieval-Augmented Generation (RAG) architecture, this tool processes a dataset of 15,000 Machine Learning research papers from ArXiv and returns highly relevant, AI-summarized insights in milliseconds.

## 🎥 Application Demo
*(Watch the AI in action: Semantic Search, Summarization, and Keyword Extraction)*

<div align="center">
  <video src="https://github.com/user-attachments/assets/443b05ac-2caf-4126-824c-c0d3599f1f65" width="800" controls="controls"></video>
</div>
<br>

## 🧠 System Architecture

The application is built on a multi-model NLP pipeline designed for speed and contextual accuracy.

* **[User Query]** ➔ **[Sentence Transformer]** (Converts query to 384-dimensional vector)
* **[Vector]** ➔ **[FAISS Database]** (Cosine Similarity search across 15,000 papers)
* **[Retrieved Paper]** ➔ Processed simultaneously by:
  * **BART-Large** (Executive Summary)
  * **KeyBERT** (Technical Keyword Extraction)
  * **Zero-Shot & NER** (Topic and Entity Tagging)
* **[Web UI]** ➔ Displays formatted insights to the user

## ⚡ Key Engineering Features

*   **Semantic Search over Lexical Search:** Instead of basic keyword matching, the system understands the contextual meaning of a query using `all-MiniLM-L6-v2` embeddings, calculating the exact mathematical distance between the query and 15,000 abstracts.
*   **Smart Vector Caching:** Generating high-dimensional embeddings for thousands of documents is computationally expensive. I implemented a local storage controller that serializes the FAISS `.index` and Pandas `.pkl` objects to disk. This optimization reduces the application's boot time from 30 minutes to under 3 seconds.
*   **GPU-Accelerated Multi-Model Pipeline:** Once a paper is retrieved, the text is processed simultaneously by multiple Hugging Face models, optimized via hardware acceleration.
*   **Interactive UI:** The backend is wrapped in a fully interactive Gradio interface with custom CSS for an accessible, professional user experience.

## 🛠️ Tech Stack
*   **Vectorization:** `sentence-transformers/all-MiniLM-L6-v2`
*   **Vector Database:** Meta FAISS (Inner Product Optimization)
*   **Generative AI:** Facebook BART (`bart-large-cnn`)
*   **Keyword Extraction:** KeyBERT
*   **Data Handling:** Pandas, NumPy, Datasets
*   **Interface:** Gradio

## 🚀 Execution Guide
1. Clone the repository.
2. Run the Jupyter Notebook / Colab file.
3. On the initial run, the script will automatically download the dataset, encode the vectors, build the FAISS index, and cache the assets locally.
4. Access the application via the generated public Gradio URL.

---
*Developed as an independent project during the AI/ML Summer Internship at Coding Blocks School of Technology (CBSOT).*
