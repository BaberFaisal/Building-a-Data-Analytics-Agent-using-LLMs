# Building a Data Analytics Agent using LLMs

This project demonstrates how to build an intelligent **data analytics agent** using **Large Language Models (LLMs)** with the `LangChain` and `Groq API` frameworks. The notebook walks you through setting up the environment, connecting to the LLM, and interacting with your data through natural language queries.

---

## Table of Contents

- [Introduction](#introduction)
- [Setup and Installation](#setup-and-installation)
- [LLM Initialization (Groq API)](#llm-initialization-groq-api)
- [Agent Preparation](#agent-preparation)
- [Conversational Data Analysis](#conversational-data-analysis)
- [Use Cases Implemented](#use-cases-implemented)
- [Technologies Used](#technologies-used)
- [How to Run](#how-to-run)

---

## Introduction

This notebook enables a **conversational interface for data analysis** using LLMs. With tools like `LangChain` and `Groq`, you can analyze data by asking natural language questions and receive actionable insights — without writing any SQL queries or manual code.

---

## Setup and Installation

Install the required Python libraries:

```bash
 pip install --upgrade numpy
 pip install --upgrade pandas
 pip install langchain_groq --quiet
 pip install pandasai --quiet
 ```
 These libraries are responsible for:
 - **pandas, numpy**: Data handling and computation
 - **langchain_groq**: Connecting with LLM through Groq API
 - **pandasai**: Conversational querying over pandas dataframes
 ## LLM Initialization (Groq API)
 To interact with the LLM, initialize it using the Groq API with LangChain:
 ```python
 from langchain_groq import ChatGroq
 llm = ChatGroq(
     temperature=0.5,
     groq_api_key="your_api_key_here",
     model_name="mixtral-8x7b-32768"
 )
 ```
 > Replace `"your_api_key_here"` with your actual Groq API key.
 ## Agent Preparation
 An agent is created using `create_pandas_dataframe_agent` from LangChain. This allows the LLM to process natural language queries on a pandas dataframe:
 ```python
 from langchain.agents.agent_tools import create_pandas_dataframe_agent
 agent = create_pandas_dataframe_agent(
     llm=llm,
     df=df,
     verbose=True
 )
 ```
 The agent interprets user prompts, performs reasoning using the LLM, and executes relevant operations on the dataframe.
 ## Conversational Data Analysis
 Once the agent is initialized, you can interact with your dataset by typing natural language questions.
 Example Queries:
 - "What are the top 5 job categories?"
 - "Find a job that requires a Master's degree and is remote."
 - "Show average salary by experience level."
 - "Give insights on salary trends by industry."
 The agent uses the LLM to understand the question, run necessary data operations, and return meaningful answers.
 ## Use Cases Implemented
 - **Job Search Filtering**: Query jobs based on title, industry, education level, remote work percentage, or experience level.
 - **Salary Insights**: Analyze salary trends based on experience, education, job title, or company size.
 - **Data Summarization**: Summarize key data patterns, such as top companies, job types, or average salaries.
 - **Natural Language Querying**: No code or SQL needed — just ask questions in plain English.
 ## Technologies Used
 - Python – Core programming language
 - pandas – Dataframe operations
 - numpy – Numerical computations
 - LangChain – LLM orchestration framework
 - Groq API – High-speed LLM inference
 - pandasai – Conversational interaction with structured data
 ## How to Run
 1. Clone or download the repository.
 2. Open the notebook `Building_a_Data_Analytics_Agent_using_LLMs.ipynb` in Jupyter or Colab.
 3. Install required dependencies (see Setup and Installation).
 4. Add your Groq API key in the appropriate cell.
 5. Load your dataset as a pandas dataframe (into `df`).
 6. Run the notebook cells in order.

