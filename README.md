# Structured LLM Outputs with Pydantic
[![Pydantic](https://img.shields.io/badge/Data-Pydantic-e92063)](https://docs.pydantic.dev/)
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![JSON](https://img.shields.io/badge/Format-JSON%20Schema-blue)](https://json-schema.org/)

## 🏗️ Project Overview
This repository demonstrates how to solve the "unstructured text" problem in Generative AI. By utilizing **Pydantic**, we can force Large Language Models (like Gemini or GPT-4) to return data in a specific, pre-defined format. This allows AI responses to be directly integrated into software applications, databases, and automated workflows without the risk of parsing errors.

---

## 🛠️ Key Technical Implementations

### 1. Schema Definition
* **Pydantic BaseModel:** Creating rigid blueprints for data extraction (e.g., extracting entity names, dates, and sentiment from a paragraph).
* **Field Descriptions:** Providing the LLM with semantic hints via `Field(description=...)` to improve extraction accuracy.

### 2. Structured Output Orchestration
* **`with_structured_output`:** Using LangChain's native method to bind schemas directly to the model, ensuring the output follows the required JSON structure.
* **Type Safety:** Converting raw API responses into Python objects with automatic type-checking (Int, String, List, etc.).

### 3. Error Handling & Validation
* **Data Verification:** Automatically validating that required fields are present and correctly formatted.
* **Fallback Logic:** Handling scenarios where the model fails to adhere to the schema.

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Data Validation:** Pydantic v2
* **Orchestration:** LangChain / LangChain-Google-GenAI
* **LLM Provider:** Google Gemini / OpenAI
* **Environment:** `python-dotenv`

