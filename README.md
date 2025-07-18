# 🤖 LLM for Healthcare (LRCH) 🚀

## 🏥 LRCH: LLM using RAG & CAG for Healthcare Applications

![Architecture Diagram](https://github.com/user-attachments/assets/09d6439d-4d7d-46c6-be69-6a2535d21a29)

---

## 🧠 Overview

**LRCH** (Language Reasoning for Clinical Help) is a healthcare-focused large language model pipeline that intelligently switches between **`Cache-Augmented Generation (CAG)`** and **`Retrieval-Augmented Generation (RAG)`** based on the confidence of domain classification. It combines curated domain knowledge and dynamic retrieval for producing reliable, semantically accurate answers in medical contexts.

---

## ⚙️ Architecture Summary

- 🗂️ **Domain Specialization via CAG**  
  - Curated Q&A pairs across **10 medical specialties** are fed into the **`LLaMA 3.1 3B`** model.
  - **`Precomputed KV caches`** are stored offline for each specialty to support faster, context-rich generation.
  - On receiving a query, if confidently classified into a domain, the corresponding static cache is loaded into the model for answer generation (**Cache-Augmented Generation**).

- 📚 **Fallback with RAG**  
  - If a query cannot be confidently mapped to a known specialty, **`RAG`** is triggered.
  - Relevant medical documents are retrieved from a domain-specific database.
  - The retrieved context is appended to the prompt for **Retrieval-Augmented Generation**.

- 🧪 **Domain Classification**  
  - A lightweight **`DistilBERT`** classifier maps each query to one of the 10 medical domains.
  - Low-confidence classifications trigger the RAG pathway instead of CAG.

- ⚡ **Model & Optimization**  
  - All generations are powered by an **`quantized LLaMA-3.1 3B`** model for efficient performance on edge devices or resource-constrained environments.

- 🔎 **Answer Evaluation**  
  - Each generated answer is evaluated using **semantic similarity** against reference answers using **`MiniLM-L6-v2`** embeddings.

---

## 📘 Technologies Used

### 🔄 Retrieval-Augmented Generation (RAG)
A method where a model retrieves external documents relevant to a query and then generates a response using both the query and the retrieved content. It boosts factual accuracy by grounding answers in real data sources.

### 🧠 Cache-Augmented Generation (CAG)
Instead of always relying on dynamic retrieval, CAG leverages **precomputed `Key-Value caches`** of domain-specific knowledge. When a query falls under a known domain, cached memory is used, making responses faster and more domain-aware.

### 🦙 LLaMA 3.1 3B (Quantized)
A state-of-the-art open LLM developed by Meta. In this project, it's quantized to `int 4` format to ensure **low memory usage** and **faster inference** without compromising quality.

---

## 🏁 Future Scope

- Add support for **multi-domain fusion** queries.  
- Incorporate **user feedback** loop for continuous learning.  
- Explore **on-device deployment** for offline clinical use-cases.  

---

## 🧑‍⚕️ Built for Smarter, Safer Healthcare AI

With LRCH, we move one step closer to **intelligent, context-aware, and resource-efficient AI** that can support real-world healthcare professionals and systems. 🌐💊

---

> 📫 **Contact**  
> Satyam Solanki |
> satyamsolanki.official@gmail.com |
> https://www.linkedin.com/in/satyam-solanki/

