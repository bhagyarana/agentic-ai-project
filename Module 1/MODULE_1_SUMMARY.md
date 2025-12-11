# Module 1: LangChain Fundamentals - Summary

## Overview
Module 1 introduces the fundamentals of LangChain, a powerful framework for building applications with Large Language Models (LLMs). This module covers the core concepts needed to get started with LangChain, including setting up OpenAI integration, working with prompts, understanding LangChain Expression Language (LCEL), and parsing outputs.

---

## Topics Covered

### 1. **LangChain with OpenAI** (`1_langchain_openai.ipynb`)
   - Setting up and configuring `ChatOpenAI` model
   - Basic LLM invocation with messages
   - Creating simple chains using `ChatPromptTemplate`
   - Environment variable management with `python-dotenv`

### 2. **Prompt Templates** (`2_prompt_templates.ipynb`)
   - **String Prompt Templates**: Simple text-based prompts with variables
   - **Chat Prompt Templates**: Structured prompts for chat models with system/user messages
   - **MessagesPlaceholder**: Managing conversation history in chatbots

### 3. **LangChain Expression Language (LCEL)** (`3_lcel.ipynb`)
   - Understanding the pipe operator (`|`) for chaining components
   - Core Runnable components:
     - `RunnablePassthrough`: Passes data through unchanged
     - `RunnableLambda`: Executes custom Python functions
     - `RunnableParallel`: Runs multiple chains in parallel
   - Building nested chains and complex workflows
   - Real-world RAG (Retrieval Augmented Generation) example

### 4. **Output Parsers** (`4_output_parser.ipynb`)
   - **StrOutputParser**: Extracts plain text from model responses
   - **JsonOutputParser**: Parses JSON-structured outputs
   - **PydanticOutputParser**: Validates and structures outputs using Pydantic models

### 5. **Sequential Chains** (`sequential_chain.ipynb`)
   - Creating multi-step chains where output of one chain feeds into the next
   - Practical example: Generating a speech title, then writing the speech

---

## Steps to Follow and Execute Module 1

### Prerequisites
1. **Python Environment**: Ensure Python 3.8+ is installed
2. **OpenAI API Key**: Obtain an API key from OpenAI (https://platform.openai.com/)
3. **Environment Setup**: Create a `.env` file in your project directory with:
   ```
   OPENAI_API_KEY=your_api_key_here
   ```

### Installation Steps

1. **Install Required Packages**
   ```bash
   pip install -r requirements.txt
   pip install python-dotenv
   ```
   
   Key packages include:
   - `langchain-openai`: OpenAI integration
   - `langchain-core`: Core LangChain functionality
   - `python-dotenv`: Environment variable management
   - `pydantic`: Data validation (for output parsers)

2. **Set Up Environment Variables**
   - Create a `.env` file in your project root
   - Add your OpenAI API key: `OPENAI_API_KEY=your_key_here`
   - Load it in notebooks: `from dotenv import load_dotenv; load_dotenv()`

### Execution Order

**Recommended sequence to follow:**

1. **Start with `1_langchain_openai.ipynb`**
   - Learn basic LLM setup and invocation
   - Understand how to create simple chains
   - Practice with basic prompts

2. **Move to `2_prompt_templates.ipynb`**
   - Master different prompt template types
   - Learn to structure prompts for chat models
   - Understand conversation history management

3. **Deep dive into `3_lcel.ipynb`**
   - Understand the pipe operator (`|`) concept
   - Practice with Runnable components
   - Build complex chains with parallel execution
   - Study the RAG example

4. **Learn `4_output_parser.ipynb`**
   - Understand why output parsing is important
   - Practice with different parser types
   - Learn structured output generation

5. **Complete with `sequential_chain.ipynb`**
   - Apply all concepts learned
   - Build a multi-step chain
   - See how chains can be combined

### Key Concepts to Master

- **Chains**: Sequences of operations that process data step-by-step
- **LCEL Syntax**: Using `|` to connect components: `prompt | model | parser`
- **Invocation**: Calling chains with `.invoke()` method
- **Prompt Engineering**: Structuring prompts for better model responses
- **Output Parsing**: Converting model outputs into usable formats

### Common Patterns

```python
# Basic Chain Pattern
chain = prompt | model | parser
result = chain.invoke({"input": "your input"})

# Sequential Chain Pattern
chain1 = prompt1 | model | parser1
chain2 = prompt2 | model | parser2
combined = chain1 | (lambda x: {"input": x}) | chain2

# Parallel Chain Pattern
parallel = RunnableParallel({
    "output1": chain1,
    "output2": chain2
})
```

---

## Learning Outcomes

After completing Module 1, you should be able to:
- ✅ Set up LangChain with OpenAI
- ✅ Create and use different types of prompt templates
- ✅ Build chains using LangChain Expression Language (LCEL)
- ✅ Parse and structure model outputs
- ✅ Create sequential and parallel chains
- ✅ Build basic RAG applications

---

## Tips for Success

1. **Experiment**: Try modifying prompts and see how outputs change
2. **Understand the Flow**: Trace how data flows through chains
3. **Read Error Messages**: LangChain provides helpful error messages
4. **Start Simple**: Begin with basic chains before building complex ones
5. **Use Output Parsers**: Always parse outputs for better control

---

## Next Steps

After mastering Module 1, you'll be ready to:
- Work with more advanced LangChain features
- Build production-ready LLM applications
- Integrate with vector databases
- Create sophisticated RAG systems
- Deploy LangChain applications

---

## Quick Reference

| Component | Purpose | Example |
|-----------|---------|---------|
| `ChatOpenAI` | LLM model wrapper | `ChatOpenAI(model="gpt-4o")` |
| `PromptTemplate` | String-based prompts | `PromptTemplate.from_template("Say {word}")` |
| `ChatPromptTemplate` | Chat message prompts | `ChatPromptTemplate.from_messages([...])` |
| `StrOutputParser` | Extract text | `StrOutputParser()` |
| `JsonOutputParser` | Parse JSON | `JsonOutputParser()` |
| `RunnablePassthrough` | Pass through data | `RunnablePassthrough()` |
| `RunnableLambda` | Custom function | `RunnableLambda(my_func)` |
| `RunnableParallel` | Parallel execution | `RunnableParallel({"a": chain1, "b": chain2})` |

---

*Happy Learning! 🚀*

