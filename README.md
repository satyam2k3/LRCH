# LRCH

![Architecture Diagram](https://github.com/user-attachments/assets/09d6439d-4d7d-46c6-be69-6a2535d21a29)


- Precompute KV caches offline for 10 medical domains by feeding curated Q&A pairs into LLaMA-3.1 3B.  
- Classify each incoming query into one of the 10 specialties using a Distil BERT model.  
- For a recognized domain, load its static cache into LLaMA to generate answers (Cache-Augmented Generation).  
- If the query isn’t confidently classified, retrieve relevant documents from a medical database and run Retrieval-Augmented Generation.  
- Use the INT4-quantized LLaMA-3.1 3B model for all answer generation.  
- Evaluate answers by computing semantic similarity against reference answers with MiniLM-L6-v2.  
