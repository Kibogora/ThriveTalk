# ThriveTalk
Conversation AI Chatbot for sharing knowledge about mental health
# Mental Health Chatbot

This repository contains the code for a mental health assistance chatbot. It uses a combination of techniques to provide answers related to mental health symptoms, prevention, and treatment based on a knowledge base.

## Overview

This chatbot leverages a retrieval-augmented generation (RAG) approach using:

*   **Knowledge Base:** A CSV file containing mental health questions and answers.
*   **Sentence Embeddings:** Sentence Transformers for semantic understanding of the questions and context.
*   **Vector Store:** ChromaDB for efficient storage and retrieval of knowledge.
*   **Large Language Model (LLM):** Groq's LLM for generating responses.
*   **Langchain:** For building the RAG pipeline.
*   **Gradio:** For a simple web UI to interact with the chatbot.

## How it Works

1.  **Data Loading and Preprocessing:**
    *   The `Mental_Health_FAQ.csv` file is loaded into a Pandas DataFrame.
    *   Context data is created by combining questions and answers from the DataFrame
2.  **Embedding Generation:**
    *   The `all-MiniLM-L6-v2` sentence transformer model is used to encode the contexts into vector embeddings.
    *   Each context is embedded into a 384-dimensional vector which represents the meaning of the text.
3.  **Vector Store Setup:**
    *   ChromaDB is used to store context data embeddings for efficient similarity search.
    *   The `mixedbread-ai/mxbai-embed-large-v1` model is used for embedding when storing data in the vector store
4.  **RAG Chain Construction:**
    *   LangChain is used to create a chain for the retrieval and generation.
        *   The user query is used to search for relevant context using the vector store.
        *   The LLM is prompted with the context and the original user query.
        *   The LLM generates a response using the Groq API.
5.  **Gradio UI:**
    *   A simple web interface using Gradio is provided for easy interaction with the chatbot.
    *   The user can input their question in the text box and get a response in real-time.

## Code Explanation

### Dependencies
The following packages are used in the code:

- pandas for data manipulation
- sentence-transformers and langchain_huggingface for embeddings
- langchain_chroma for vector storage
- langchain_groq for the LLM
- langchain_core for building the RAG pipeline
- gradio for the web interface

Install the dependencies using pip:
```bash
pip install pandas sentence-transformers langchain_huggingface langchain_chroma langchain_groq langchain_core gradio
