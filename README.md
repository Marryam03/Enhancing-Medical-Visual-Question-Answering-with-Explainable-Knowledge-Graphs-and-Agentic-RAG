# Enhancing Medical Visual Question Answering with Explainable Knowledge Graphs and Agentic RAG

This repository contains two main modules for advancing explainable Medical Visual Question Answering (VQA): **KG&RAG** (Knowledge Graph & Retrieval-Augmented Generation) and **AgenticRAG** (Agentic Retrieval-Augmented Generation). Both modules are designed to improve answer accuracy and provide transparent, rationale-driven explanations for medical images.

---

## 1. KG&RAG

### Overview

The **KG&RAG** module integrates structured medical knowledge graphs with retrieval-augmented generation to answer medical VQA tasks. It leverages both explicit knowledge (from graphs) and implicit knowledge (from large language models) to provide accurate and explainable answers to both closed-ended and open-ended medical questions about images.


### Workflow

1. **Data Preparation**: Medical VQA datasets are loaded, containing images, questions, answer choices, and ground-truth solutions.
2. **Knowledge Graph Construction**: Medical knowledge is structured into a graph, encoding relationships between entities (e.g., diseases, findings, anatomical structures).
3. **Retrieval-Augmented Generation**:
   - For each question, relevant context is retrieved from the knowledge graph and/or external sources.
   - The retrieved context is fed into a language model (e.g., Deepseek, Gemini) to generate an answer and a rationale.
4. **Answer & Rationale Extraction**: The model's output is parsed to separate the final answer and the supporting rationale.
5. **Evaluation**:
   - **Closed-ended**: Accuracy is computed as the percentage of correct answers.
   - **Open-ended**: BERTScore (Precision, Recall, F1) is used to compare generated answers and rationales to ground-truth solutions.

### Evaluation Score from Deepseek with KG & RAG:

- **Closed-ended**:  
  - Final-Answer Accuracy: 79.39%
  - Rationale BERTScore-F1: 85.57%
- **Open-ended**:  
  - Final-Answer BERTScore-F1: 87.82%
  - Rationale BERTScore-F1: 84.81%


## 2. AgenticRAG

### Overview

The **AgenticRAG** module explores an agentic approach to retrieval-augmented generation for medical VQA. It focuses on not only retrieving relevant context but also on agent-like reasoning and stepwise explanation, aiming for more transparent and trustworthy answers.


### Workflow

1. **Data Loading**: The results CSV is loaded, containing predicted answers, true answers, generated rationales, and true solutions.
2. **Agentic Reasoning**: The model is prompted or architected to reason step-by-step, providing both an answer and a detailed rationale for each question.
3. **Evaluation**:
   - **Closed-ended**: Accuracy and BERTScore (F1, Precision, Recall) are computed for both answers and rationales.
   - **Open-ended**: BERTScore is used to assess the semantic similarity of generated answers/rationales to ground-truth.
   - The evaluation script infers question type (closed/open) based on the answer format (e.g., "yes"/"no" for closed).
   - Results are summarized for both question types.

### Evaluation Score from Gemini with KG & Agentic RAG:

- **Closed-Ended Questions**:
  - Accuracy: 62.59%
  - BERTScore F1 (Answer): 0.8525
  - BERTScore F1 (Rationale): 0.6143
- **Open-Ended Questions**:
  - Accuracy: 25.00%
  - BERTScore F1 (Answer): 0.5161
  - BERTScore F1 (Rationale): 0.5872
