The Empathetic AI Companion
Key Features

Stateful Memory (SQLite): Uses a local SQLite database to store per-user chat history. Stan can recall details from previous sessions even after a system restart.
Responsive Dashboard: A custom-themed Gradio UI with system status cards and quick-action buttons, optimized for mobile and desktop.
Robust Error Handling: Implements exponential backoff and retry logic to handle API rate limits (429 errors) gracefully.

Technical Stack
LLM: Google Gemini 1.5 Flash (via LangChain)
Framework: LangChain (for message handling and prompt templates)
Database: SQLite3 (for persistent, cost-efficient stateful storage)
Frontend: Gradio (with custom CSS for responsiveness)
Environment: Python 3.10+ / Google Colab

Architecture Overview
The system follows a Stateless Logic with Stateful Store design to minimize runtime costs while maximizing context retention:
User Input: Captured via the Gradio interface.
Context Retrieval: The system queries the SQLite DB for the last N messages.
Inference: A composite prompt (System Persona + History + New Input) is sent to Gemini 1.5-Flash.
Persistence: Both the user query and Stan's reply are saved back to SQLite before being displayed.
Getting Started

1. Prerequisites
Python 3.8+
A Google Gemini API Key (stored in Colab Secrets as GEMINI_API_KEY)

3. Installation
Bash

pip install -U langchain-google-genai gradio sqlite3
3. Running the Bot
Simply run the main script. The UI will generate a public .gradio.live link for sharing.

Python

python stan_bot.py
📊 Evaluation Criteria Met
[x] Empathy & Consistency: Stan adapts his tone and maintains his identity.

[x] Memory Recall: Tested across restarts using SQLite.

[x] Modular Design: Logic is encapsulated in the StanChatBot class, ready to plug into any UGC platform.

[x] Cost Optimization: Efficient token usage by limiting history retrieval and using 1.5-Flash.
