# 📌 Project Title: CodeSage – AI-Powered Code Reviewer  

## 🚀 Project Overview  
**CodeSage** is an AI-powered assistant that reviews source code, detects potential bugs, and suggests performance improvements. It leverages Large Language Models (LLMs) with prompt engineering techniques to analyze code and provide structured, developer-friendly feedback.  

The project explores advanced prompting methods such as zero-shot, one-shot, multi-shot, dynamic prompting, and chain-of-thought prompting to enhance review accuracy. Additionally, it integrates embeddings and vector databases to retrieve relevant past bug fixes, making recommendations context-aware.  

## 🔧 Features  
- **Error Detection & Suggestions** – Identifies syntax, logical, and optimization issues.  
- **Structured Output** – Returns feedback in JSON for easy integration.  
- **Prompt Engineering** – Implements zero-shot, one-shot, multi-shot, dynamic, and chain-of-thought prompting.  
- **Evaluation Pipeline** – Uses a dataset of code snippets to benchmark outputs against expected fixes.  
- **Similarity Search** – Embeddings + vector database to match bugs with prior solutions.  
- **Function Calling** – `analyzeCode(language, snippet)` to automate code review.  

## 🎯 Tech Stack  
- **Backend**: Node.js / Python  
- **LLM**: OpenAI / Hugging Face API  
- **Database**: Vector DB (Pinecone / FAISS)  
- **Evaluation**: Custom testing framework with similarity metrics (Cosine, L2, Dot Product).  

## 📈 Future Scope  
- Multi-language support  
- Integration with GitHub/GitLab CI/CD for automated pull request reviews  