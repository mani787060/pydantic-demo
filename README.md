# Structured LLM Outputs with Pydantic

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Pydantic](https://img.shields.io/badge/Data%20Validation-Pydantic-e92063)
![LangChain](https://img.shields.io/badge/Framework-LangChain-green)
![Generative AI](https://img.shields.io/badge/Domain-Generative%20AI-purple)

A hands-on Generative AI project demonstrating how to convert unstructured LLM responses into structured, validated Python objects using Pydantic and LangChain.

## 📌 Project Overview

Large language models can generate useful answers, but their responses are often unstructured text. This can make it difficult to use the results directly in applications, databases, or automated workflows.

**Pydantic** helps solve this problem by defining a schema that describes the expected structure and data types of a response. When integrated with LangChain's structured-output capabilities, it can help applications obtain data in a predictable format.

This project explores the fundamentals of schema definition, structured generation, type validation, and error handling in LLM applications.

## 🎯 Project Objectives

- Understand how Pydantic models define structured data.
- Learn how to use `BaseModel` and `Field`.
- Explore structured-output integration with LangChain.
- Convert model responses into validated Python objects.
- Understand validation errors and how to handle them.
- Build a foundation for reliable LLM-powered data extraction.

## ✨ Key Features and Concepts

### 1. Pydantic Schema Definition

Pydantic's `BaseModel` lets you define the fields and types expected in a response.

For example:

```python
from pydantic import BaseModel, Field

class EntityExtraction(BaseModel):
    name: str = Field(description="Name of the person or organization")
    date: str = Field(description="Date mentioned in the text")
    sentiment: str = Field(description="Sentiment expressed in the text")
```

The schema provides a clear structure for the expected data. In a real application, date and sentiment fields can use stricter types or constraints when appropriate.

### 2. Structured LLM Outputs

LangChain supports structured-output workflows that connect an LLM to a defined schema.

A typical pattern is:

```python
structured_model = model.with_structured_output(EntityExtraction)
result = structured_model.invoke(
    "Alex joined the company on 12 March 2026 and expressed excitement."
)
```

Here, `model` represents a compatible LangChain chat model that has already been initialized.

The returned result can be a validated Pydantic object, depending on the model integration and configuration. The exact behavior should be checked against the provider and LangChain versions being used.

### 3. Field Descriptions

Pydantic's `Field(description=...)` can explain what each field should contain. Clear descriptions help communicate the intended schema to supported structured-output integrations.

### 4. Type Checking and Validation

Pydantic validates data against the declared schema. For example, it can check whether required fields are present and whether values match their expected types.

Validation helps catch formatting and type errors, but it does not guarantee that the model's extracted information is factually correct.

### 5. Error Handling

Structured-output applications should account for:
- Missing or invalid fields.
- Responses that do not match the expected schema.
- API failures and rate limits.
- Model-specific structured-output limitations.

Depending on the integration, errors may occur during model invocation or validation. Handle these cases explicitly rather than assuming every response will be valid.

## 🧰 Tech Stack

- **Language:** Python
- **Data Validation:** Pydantic
- **LLM Framework:** LangChain
- **Model Integration:** Provider-specific LangChain integration, such as Google Gemini or OpenAI, if configured
- **Configuration:** `python-dotenv`, if used by the implementation

## ⚙️ Getting Started

### Prerequisites

- Python installed on your system.
- An API key for the LLM provider used in the project.
- The required LangChain and provider dependencies.

### 1. Clone the Repository

```bash
git clone https://github.com/mani787060/pydantic-demo.git
cd pydantic-demo
```

### 2. Install Dependencies

Install the packages required by your Python file. A possible starting point is:

```bash
pip install pydantic langchain-core langchain-google-genai python-dotenv
```

If the implementation uses OpenAI or another provider, install the corresponding integration instead. For reproducible setup, use the project's tested dependency versions.

### 3. Configure Environment Variables

If your code loads credentials from a `.env` file, create one in the project directory:

```env
GOOGLE_API_KEY=your_api_key_here
```

Use the variable name expected by your script. Add `.env` to `.gitignore` to protect your API key.

### 4. Run the Project

```bash
python your_filename.py
```

Replace `your_filename.py` with the actual Python filename in your repository.

## 🧠 What You Will Learn

- Defining data schemas with Pydantic.
- Using `BaseModel` and `Field`.
- Connecting structured-output schemas to chat models.
- Working with typed Python objects instead of raw text.
- Handling validation failures and API errors.
- Designing more predictable LLM application workflows.

## 🌍 Practical Applications

Structured LLM outputs can support:
- Information and entity extraction.
- Resume and document parsing.
- Sentiment classification.
- Customer-support ticket categorization.
- Data transformation and automation.
- Structured responses in RAG and agentic AI systems.

## 🔮 Future Improvements

- Add stricter field types, enums, and custom validators.
- Include automated tests for valid and invalid responses.
- Compare structured-output support across model providers.
- Add retry logic and clear validation-error reporting.
- Export validated results to JSON, CSV, or a database.
- Integrate the schema into a RAG or agentic AI workflow.

## 📝 Conclusion

Pydantic provides a clear way to define and validate the structure of data used in Python applications. When combined with compatible LLM integrations, it can make AI-generated outputs easier to process and integrate into software systems.

This project provides a foundation for building more structured and maintainable Generative AI applications.

## 👨‍💻 Author

**Mani Ratan**

- GitHub: [@mani787060](https://github.com/mani787060)

---

*Part of a hands-on learning journey into Generative AI, LangChain, and reliable LLM application development.*
