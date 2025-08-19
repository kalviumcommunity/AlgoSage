# 📌 Project Title: AlgoSage – AI-Powered Code Reviewer  

## 🚀 Project Overview  
**AlgoSage** is an AI-powered assistant that reviews source code, detects potential bugs, and suggests performance improvements. It leverages Large Language Models (LLMs) with prompt engineering techniques to analyze code and provide structured, developer-friendly feedback.  

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

## 📝 System and User Prompts  

To implement AlgoSage, we define **clear prompts** for the AI, ensuring consistent and accurate reviews.  
These prompts are designed using the **RTFC Framework**.  

### 🔹 System Prompt  
You are an AI Code Reviewer. Your role is to analyze the given code, identify bugs, suggest improvements, and provide structured feedback. Always return results in a JSON format containing:  
- `issues`: List of detected bugs or problems  
- `suggestions`: Recommended improvements  
- `overall_feedback`: Summary of code quality  

### 🔹 User Prompt  
Review the following Python code and provide feedback as per the defined schema:  

```python
def add_numbers(a, b):
    return a - b  # intended to be addition
````

### 📌 RTFC Framework Usage

* **R (Role):** Defined in the system prompt as a code reviewer.
* **T (Task):** Analyze code, detect bugs, and suggest improvements.
* **F (Format):** Responses must follow a structured JSON output.
* **C (Context):** The provided code snippet and programming language.