# TripBuddy – AI Travel Planning Assistant

TripBuddy is an AI-powered travel assistant built with **Python, LangChain, LangGraph, and OpenAI GPT-4o-mini**.

It uses an LLM agent with external tools to answer travel-related questions such as **destination weather, currency conversion, and estimated trip costs**. It also supports conversation memory for follow-up questions.

## Features

* 🌤️ **Weather Information** – Get weather information for a destination and date.
* 💱 **Currency Conversion** – Convert currencies using a real-time exchange-rate API.
* 💰 **Trip Cost Estimation** – Estimate travel costs based on destination, number of days, and travel style.
* 🛠️ **Tool Calling** – The AI decides when an external tool is required to answer a question.
* 💬 **Conversation Memory** – Supports follow-up questions while maintaining conversation context.
* 🔄 **Multi-Tool Queries** – Can use multiple tools when required for a single query.
* ⚠️ **Error Handling** – Handles invalid tool inputs and API-related errors.

## Technologies Used

* Python
* OpenAI GPT-4o-mini
* LangChain
* LangGraph
* LangChain Tools
* REST APIs
* Open-Meteo API
* Frankfurter API
* Conversation Memory

## How It Works

```text
                 User Query
                     |
                     v
              OpenAI GPT-4o-mini
                     |
             Decides whether
              tools are needed
                /          \
              No            Yes
              |              |
              v              v
        Final Response   Execute Tool(s)
                              |
              +---------------+---------------+
              |               |               |
              v               v               v
           Weather         Currency       Trip Cost
             Tool           Tool            Tool
              |               |               |
              +---------------+---------------+
                              |
                              v
                    Tool Results Returned
                              |
                              v
                    OpenAI GPT-4o-mini
                              |
                              v
                       Final Response
```

## Available Tools

### 1. Weather Tool

Uses the **Open-Meteo API** to obtain weather information.

The tool can provide:

* Destination
* Date
* Minimum temperature
* Maximum temperature
* Rain probability

### 2. Currency Conversion Tool

Uses the **Frankfurter API** for currency conversion.

Example:

```text
Convert 500 USD to EUR
```

### 3. Trip Cost Estimation Tool

Estimates the approximate cost of a trip based on:

* Destination
* Number of days
* Travel style

Supported travel styles:

* Budget
* Mid-range
* Luxury

## LangGraph Workflow

The LangGraph implementation uses a simple agent workflow:

```text
START
  |
  v
Call Model
  |
  v
Tool Required?
  |              |
 No             Yes
  |              |
  v              v
 END        Execute Tools
                 |
                 v
            Call Model
                 |
                 v
                END
```

The LangGraph implementation uses:

* `StateGraph`
* `MessagesState`
* Model node
* Tool execution node
* Conditional routing
* `MemorySaver` for conversation memory

## Project Files

```text
TripBuddy/
│
├── tripbuddy_python.py
├── tripbuddy_langchain.ipynb
├── tripbuddy_langgraph.ipynb
└── README.md
```

### `tripbuddy_python.py`

Contains the Python implementation of the TripBuddy project.

### `tripbuddy_langchain.ipynb`

Contains the LangChain-based implementation using an AI agent and tools.

### `tripbuddy_langgraph.ipynb`

Contains the LangGraph-based implementation with an explicit agent workflow, tool execution, conditional routing, and conversation memory.

## Example Queries

```text
What will the weather be like in Paris on 15 October?

Convert 100 USD to EUR.

How much would a 5-day budget trip to Paris cost?

What is the weather in Tokyo and convert 500 USD to JPY?
```

## Conversation Memory

TripBuddy supports follow-up questions by maintaining conversation context.

Example:

```text
User: What is the weather in Paris?

TripBuddy: The weather information for Paris is ...

User: What about the currency?

TripBuddy: The currency used in Paris is Euro (EUR).
```

## Installation

Clone the repository:

```bash
git clone <https://github.com/Hemanth08-M>
cd TripBuddy
```

Install the required packages:

```bash
pip install -U openai langchain langchain-core langchain-openai langgraph requests python-dotenv
```

## API Key Setup

Create a `.env` file in the project directory:

```env
OPENAI_API_KEY=your_api_key_here
```

Make sure the `.env` file is not uploaded to GitHub.

You can add it to `.gitignore`:

```text
.env
```

## Running the Project

### Python File

Run:

```bash
python tripbuddy_python.py
```

### LangChain Notebook

Open:

```text
tripbuddy_langchain.ipynb
```

and run the notebook cells.

### LangGraph Notebook

Open:

```text
tripbuddy_langgraph.ipynb
```

and run the notebook cells.

## Author

**Hemanth M**

B.E. Electronics and Communication Engineering
KIT – Kalaignarkarunanidhi Institute of Technology

GitHub: **Hemanth08-M**
