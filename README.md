# 🤖 Watson - Egyptian Arabic Finance Assistant AI Agent

**Watson** is an AI-powered financial tracking assistant designed to log and manage personal financial transactions using Egyptian Arabic natural language prompts. Built on top of **n8n** and **LangChain**, Watson links a local Large Language Model (LLM) with a cloud database to ensure secure, strict, and precise expense management without hallucination.

![Watson Workflow Preview](./workflow-preview.png)

---

## 🌟 Key Features

* **Egyptian Arabic Understanding:** Seamlessly parses natural everyday Egyptian Arabic phrases for financial operations.
* **Local LLM Privacy:** Powered by **Llama 3.2** via **Ollama** for fast inference and data privacy.
* **Structured Data Persistence:** Integrates directly with **Airtable** to record, match, and update payment entries accurately.
* **Conversational Memory:** Retains a context window of up to 25 chat interactions for smooth follow-ups.
* **Strict Anti-Hallucination Rules:**
  * Zero tolerance for making up names, dates, or monetary amounts.
  * Restricted from performing independent financial calculations or offering unprompted advice.
  * Operates strictly based on tool outputs.

---

## 🛠️ Tech Stack

* **Workflow Automation:** [n8n](https://n8n.io/)
* **AI & Agentic Framework:** LangChain (`@n8n/n8n-nodes-langchain`)
* **LLM Provider:** Ollama (`llama3.2:latest`)
* **Database Integration:** Airtable (Personal Access Token API)

---

## 🏗️ Workflow Architecture

The n8n workflow consists of the following key nodes:

1. **When Chat Message Received (Chat Trigger):** Entry point for user interactions.
2. **AI Agent:** The decision-making core routing queries between model and tools.
3. **Simple Memory (Window Buffer):** Maintains context across 25 turns.
4. **Ollama Chat Model:** Llama 3.2 instance bound with strict system instructions.
5. **Payment DB (Airtable Tool):** Handles `upsert` database operations for Name, Amount, Date, and IDs.

---

## 🚀 Getting Started

### Prerequisites
* Running instance of **n8n** (Self-hosted / Docker).
* **Ollama** installed locally with `llama3.2` model downloaded (`ollama run llama3.2`).
* An **Airtable** base configured for tracking payments.

### Installation Steps
1. Download or clone the `workflow.json` file from this repository.
2. Open your **n8n** dashboard.
3. Select **Workflows** → **Import from File**, then upload `workflow.json`.
4. Configure your credentials in n8n:
   * **Ollama API Credentials**
   * **Airtable Personal Access Token**
5. Link your Airtable Base and Table IDs inside the *Payment DB* node.
6. Activate the workflow and test **Watson** via the chat trigger!

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
