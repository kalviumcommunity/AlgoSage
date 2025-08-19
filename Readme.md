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

## 🎯 Zero-Shot Prompting  

In AlgoSage, we apply **Zero-Shot Prompting**, where the AI is asked to perform the task without any prior examples.  
Instead of showing sample inputs/outputs, the AI directly relies on the instructions to understand the task.  
This makes the system **flexible, adaptive, and language-agnostic**.  

### 🔹 Zero-Shot Prompt  

**System Prompt:**  
You are an AI code reviewer. Analyze the given code, detect bugs, and suggest improvements.  
Always return results in JSON format with three fields: `issues`, `suggestions`, and `overall_feedback`.  

**User Prompt:**  
Review the following JavaScript code and provide structured feedback:  

```javascript
function addition(a, b) {
    return a + b; // intended to be addition 
}
````

### 📌 Why Zero-Shot Prompting?

* The AI is not given examples — only task-specific instructions.
* It can generalize across **multiple programming languages** and scenarios.
* Ensures **scalable code reviews** without needing predefined cases.



## 🎯 One-Shot Prompting  

In AlgoSage, we use **One-Shot Prompting**, where the AI is given a **single example** before performing the task.  
This helps guide the model with a reference while still keeping it generalizable.  

### 🔹 One-Shot Prompt  

**System Prompt:**  
You are an AI code reviewer. Analyze the given code, detect bugs, and suggest improvements.  
Always return results in JSON format with three fields: `issues`, `suggestions`, and `overall_feedback`.  

**User Prompt (with one example):**  

Example Input (Python):  
```python
def divide(a, b):
    return a * b  # intended to be division
````

Example Expected Output (JSON):

```json
{
  "issues": ["The operator used is multiplication instead of division."],
  "suggestions": ["Replace '*' with '/' to correctly divide the numbers."],
  "overall_feedback": "Logic error detected in the function implementation."
}
```

Now review the following Java code:

```java
public int subtract(int a, int b) {
    return a + b; // intended to be subtraction
}
```

### 📌 Why One-Shot Prompting?

* Provides **one guiding example** to set the response pattern.
* Ensures the AI generates **consistent, structured outputs**.
* Reduces ambiguity compared to zero-shot prompting.


## 🎯 Multi-Shot Prompting  

In AlgoSage, we apply **Multi-Shot Prompting**, where the AI is provided with **multiple examples** before being asked to solve the real task.  
This method ensures the AI clearly understands the **pattern, structure, and expectations** of the output.  

### 🔹 Multi-Shot Prompt  

**System Prompt:**  
You are an AI code reviewer. Analyze the given code, detect bugs, and suggest improvements.  
Always return results in JSON format with three fields: `issues`, `suggestions`, and `overall_feedback`.  

**User Prompt (with multiple examples):**  

Example 1 (Python):  
```python
def add(a, b):
    return a - b  # intended to be addition
````

Expected Output:

```json
{
  "issues": ["The operator used is subtraction instead of addition."],
  "suggestions": ["Replace '-' with '+' to correctly add the numbers."],
  "overall_feedback": "Logic error detected in the addition function."
}
```

Example 2 (JavaScript):

```javascript
function square(n) {
    return n + n; // intended to be square
}
```

Expected Output:

```json
{
  "issues": ["The function doubles the number instead of squaring it."],
  "suggestions": ["Replace 'n + n' with 'n * n' to correctly square the number."],
  "overall_feedback": "Incorrect mathematical operation for squaring."
}
```

Now review the following C++ code:

```cpp
int multiply(int a, int b) {
    return a - b; // intended to be multiplication
}
```

### 📌 Why Multi-Shot Prompting?

* Gives the AI **multiple reference patterns** to ensure consistent results.
* Helps in **complex tasks** where one example isn’t enough.
* Reduces errors and improves **accuracy of code reviews**.

## 🎯 Dynamic Prompting  

In AlgoSage, we use **Dynamic Prompting**, where the prompt is automatically adapted based on the **user’s input context** (e.g., programming language, code style, or desired output format).  
This makes the system **flexible and personalized**, instead of relying on fixed instructions.  

### 🔹 Dynamic Prompt Example  

**System Prompt (Template):**  
You are an AI code reviewer. Analyze the given code in **{{language}}**, detect bugs, and suggest improvements.  
Always return results in JSON format with three fields: `issues`, `suggestions`, and `overall_feedback`.  

**User Prompt (Generated Dynamically):**  
Review the following **{{language}}** code:  

```{{language}}
{{code_snippet}}
````

### Example Execution

If the user provides **Python code**:

```python
def divide(a, b):
    return a * b  # intended to be division
```

The dynamically generated prompt becomes:

```text
You are an AI code reviewer. Analyze the given code in Python, detect bugs, and suggest improvements.
Always return results in JSON format with three fields: issues, suggestions, and overall_feedback.

Review the following Python code:
def divide(a, b):
    return a * b  # intended to be division
```

Expected Output:

```json
{
  "issues": ["The function multiplies instead of dividing."],
  "suggestions": ["Replace '*' with '/' to correctly perform division."],
  "overall_feedback": "Incorrect operator used for division."
}
```

### 📌 Why Dynamic Prompting?

* Automatically adapts prompts to **any programming language**.
* Makes the system more **scalable and user-specific**.
* Reduces manual work while ensuring **consistent structured outputs**.