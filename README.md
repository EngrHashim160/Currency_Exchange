# Currency Exchange Tool

A Python-based tool for currency conversion using LangChain and Groq LLM integration.

## Overview

This project demonstrates how to build a currency conversion tool using LangChain's tool framework and Groq's LLM capabilities. The tool allows users to:

1. Fetch real-time currency conversion rates between any two currencies
2. Convert amounts between currencies using the fetched rates
3. Interact with the tool using natural language through an LLM interface

## Features

- **Real-time Exchange Rates**: Fetches current exchange rates from ExchangeRate-API
- **Currency Conversion**: Performs accurate currency conversions based on current rates
- **LLM Integration**: Uses Groq's LLM to understand natural language requests for currency conversion
- **Tool Binding**: Demonstrates LangChain's tool binding capabilities for AI assistants

## Requirements

- Python 3.11+
- LangChain libraries
- Groq API key
- Internet connection for API access

## Dependencies

```
langchain-core
langchain-groq
requests
python-dotenv
```

## Setup

1. Clone this repository
2. Install the required dependencies:
   ```
   pip install langchain-core langchain-groq requests python-dotenv
   ```
3. Create a `.env` file with your Groq API key:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

## Usage

The project is implemented as a Jupyter notebook (`currency_exchange_tool.ipynb`) that demonstrates:

1. Creating custom tools for currency conversion
2. Binding these tools to a Groq LLM
3. Processing natural language requests for currency conversion
4. Handling the tool execution flow

Example usage:
```python
# Initialize the LLM with tools
llm = ChatGroq(model_name="deepseek-r1-distill-llama-70b")
llm_with_tools = llm.bind_tools([get_conversion_factor, convert])

# Ask a question about currency conversion
messages = [HumanMessage('What is the conversion factor between INR and USD, and based on that can you convert 10 inr to usd')]
response = llm_with_tools.invoke(messages)
```

## How It Works

1. The `get_conversion_factor` tool fetches the current exchange rate between two currencies
2. The `convert` tool performs the mathematical conversion using the rate
3. The LLM understands the user's request and orchestrates the appropriate tool calls
4. Results are returned to the user in a conversational format

## API Used

This project uses the ExchangeRate-API for fetching current exchange rates. For production use, you should register for your own API key at [ExchangeRate-API](https://www.exchangerate-api.com/).

## License

MIT

## Acknowledgements

- [LangChain](https://github.com/langchain-ai/langchain) for the LLM framework
- [Groq](https://groq.com/) for the LLM API
- [ExchangeRate-API](https://www.exchangerate-api.com/) for currency exchange data