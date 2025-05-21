# Snowflake CineBot

---

The Snowflake CineBot is a powerful conversational AI application designed to provide movie recommendations and answer movie-related questions. It leverages the robust capabilities of **Snowflake Native Apps** and the **Snowflake Cortex Suite** to deliver an intelligent and interactive user experience.

## Product Overview

The CineBot project demonstrates how to integrate advanced AI functionalities, specifically **Snowflake Cortex Search Service**, into a **Snowflake Native Application**. This allows for the efficient deployment of sophisticated data processing and AI capabilities directly to consumers within their Snowflake accounts.

At its core, the CineBot functions as a **Retrieval-Augmented Generation (RAG)** system. It retrieves relevant movie information from a curated dataset within Snowflake and then uses a large language model (LLM) from Snowflake Cortex to generate human-like responses and recommendations.

## Key Features

The CineBot offers a range of features designed to enhance movie discovery and interaction:

* **Intelligent Movie Recommendations:** Get personalized movie suggestions based on your queries, including recommendations for similar movies or those within the same genre.
* **Conversational Interface:** Interact with the bot using natural language through a user-friendly chat interface powered by **Streamlit**.
* **Contextual Understanding:** The bot utilizes chat history to maintain context during a conversation, leading to more accurate and relevant responses.
* **Snowflake Cortex Integration:** Seamlessly integrates with Snowflake Cortex for advanced AI capabilities, including:
    * **Vector Search:** Efficiently search through movie data using the **Cortex Search Service** to find relevant information.
    * **`snowflake.cortex.complete` function:** Leverages Snowflake's built-in language models (Mistral Large, Snowflake Arctic, Llama3) for generating conversational responses and summarizing information.
* **Scalable and Secure Deployment:** Built as a **Snowflake Native App**, ensuring secure and scalable deployment directly within the Snowflake ecosystem.
* **Data Chunking for RAG:** The application intelligently chunks movie overview text to optimize retrieval performance for the RAG system.

## Functionalities

The CineBot provides the following core functionalities:

* **Movie Data Ingestion and Preparation:**
    * Ingests movie metadata from a CSV file into a Snowflake table (`MOVIES_METADATA`).
    * Transforms the raw movie data into a structured format (`movies_raw`).
    * **Text Chunking:** Utilizes a Python UDF (`core.text_chunk`) to break down long movie overviews into smaller, manageable chunks, which is crucial for efficient vector search. Each chunk is associated with relevant movie attributes like title, budget, popularity, and runtime.
* **Cortex Search Service Creation and Management:**
    * Creates a **Cortex Search Service** (`movies_recommendation_service`) on the chunked movie data. This service enables fast and relevant retrieval of movie information based on user queries.
    * Manages the lifecycle of the search service within the Snowflake environment.
* **Interactive Streamlit UI:**
    * Presents a web-based chat interface built with **Streamlit** (`ui.py`).
    * Allows users to type in questions and receive responses from the bot.
    * Provides configuration options in the sidebar for advanced users, such as:
        * **Selecting a Cortex Search Service:** Choose from available search services.
        * **Clearing Conversation:** Reset the chat history.
        * **Debug Mode:** Enable a debug view to inspect context documents and chat history summaries.
        * **Chat History Usage:** Toggle whether the bot should consider previous messages for context.
        * **Model Selection:** Choose from different Snowflake Cortex models (e.g., `mistral-large`, `snowflake-arctic`, `llama3-70b`, `llama3-8b`).
        * **Context Chunk Control:** Adjust the number of retrieved context chunks used by the LLM.
        * **Chat Message History Control:** Configure the number of past chat messages considered for context.
* **Intelligent Prompt Engineering:**
    * Dynamically constructs prompts for the LLM by combining the user's question, retrieved context from the Cortex Search Service, and a summary of the chat history (if enabled).
    * Employs a prompt structure designed to instruct the LLM to act as a helpful movie recommendation chatbot with RAG capabilities.
* **Session Management:**
    * Maintains chat messages and configuration settings within the Streamlit session state for a persistent user experience.

## Architecture

The project's architecture is centered around Snowflake's capabilities:

* **Snowflake Native App:** The entire application is packaged and deployed as a Snowflake Native App, allowing for secure and streamlined distribution and installation within consumer Snowflake accounts.
* **Snowflake Cortex:** Provides the underlying AI capabilities for text generation (LLMs) and vector search.
* **Snowpark:** The Python UDFs and Streamlit application utilize Snowpark for seamless integration with Snowflake data and compute.
* **Streamlit:** Powers the interactive user interface, providing a familiar and easy-to-use conversational experience.

## Getting Started

To get started with the Snowflake CineBot, please refer to the comprehensive [QuickStart Guide](https://quickstarts.snowflake.com/guide/build-a-cinebot-with-snowflake-native-apps-and-cortex/index.html). This guide provides detailed instructions on:

* Prerequisites
* Environment setup
* Step-by-step deployment
* Instructions for interacting with the CineBot

## Licensing

This project is licensed under the **Apache License, Version 2.0**. For full details, please refer to the `LICENSE` file within this repository.


