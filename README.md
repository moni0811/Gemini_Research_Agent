# Gemini_Research_Agent

# **Multi-Tool AI Research Agent using Gemini 1.5 Flash, LangGraph, and Multiple APIs**

**🧠 Project Overview**

This project demonstrates how to build an intelligent research assistant that combines multiple data sources and tools to provide comprehensive, well-structured research reports. It integrates Google's Gemini 1.5 Flash model for natural language processing, LangGraph for building structured workflows, and various APIs including ArXiv papers, web search, weather data, and semantic search capabilities.

**✨ Features**

* **Multi-Modal Research**: Combines ArXiv papers, web search, weather data, and specialized AI research database
* **RAG-Powered Search**: Uses Pinecone vector database with semantic search for AI research papers
* **Real-time Weather Information**: Integrated OpenWeatherMap API for weather queries
* **Web Search Integration**: Google Search API through SerpAPI for general knowledge
* **ArXiv Paper Retrieval**: Direct access to research paper abstracts and content
* **Intelligent Tool Selection**: Automatically chooses appropriate tools based on query type
* **Structured Report Generation**: Professional research reports with introduction, methodology, findings, and sources
* **Rate Limiting Protection**: Built-in safeguards to respect API limits and prevent infinite loops
* **Stateful Workflow Management**: LangGraph orchestrates complex multi-step research processes

**🧩 Technologies Used**

* `langchain_google_genai` - Google Gemini integration
* `langchain_community` - Community tools and integrations
* `langgraph` - Graph-based workflow orchestration
* `datasets` - Hugging Face datasets for ArXiv papers
* `pinecone-client` - Vector database for semantic search
* `serpapi` - Google Search API integration
* `pyowm` / `openweathermap` - Weather data retrieval
* `requests` - HTTP client for web scraping
* `tqdm` - Progress bars for batch processing
* `google.generativeai` - Direct Gemini API access

**🔧 How It Works**

1. **Initialization**: The script prompts for API keys (Gemini, Pinecone, SerpAPI, OpenWeatherMap) and stores them in environment variables.

2. **Vector Database Setup**: 
   * Creates a Pinecone index for AI research papers
   * Embeds ArXiv paper content using Google's embedding model
   * Stores semantic chunks with metadata for retrieval

3. **Agent State Management**: `AgentState` typed dictionary tracks:
   * User input and chat history
   * Intermediate research steps
   * Tool execution results

4. **Tool Arsenal**: Six specialized tools are available:
   * **RAG Search**: Semantic search through AI research papers
   * **RAG Search Filter**: Targeted search within specific papers
   * **ArXiv Fetch**: Direct paper abstract retrieval
   * **Web Search**: General knowledge via Google Search
   * **Weather Agent**: Real-time weather information
   * **Final Answer**: Structured report generation

5. **Intelligent Orchestration**: The LangGraph workflow includes:
   * **Oracle Node**: Gemini analyzes queries and selects appropriate tools
   * **Router Function**: Determines next action based on tool results
   * **Tool Nodes**: Execute specific research tasks
   * **Loop Prevention**: Tracks tool usage to prevent infinite cycles

6. **Query Processing**: 
   * Analyzes user input to determine research strategy
   * Executes tools in optimal sequence
   * Synthesizes results into comprehensive reports

7. **Report Generation**: Creates structured output with:
   * Introduction and research methodology
   * Main findings and analysis
   * Conclusions and sources

**🚀 Getting Started**

1. **Clone the repository**:
```bash
git clone https://github.com/moni0811/gemini-research-agent.git
cd gemini-research-agent
```

2. **Install dependencies**:
```bash
pip install datasets google-generativeai langchain-google-genai pinecone-client langchain-core langchain-community langgraph serpapi requests tqdm pyowm
```

3. **Set up API keys**:
   * Get your Gemini API key from Google AI Studio
   * Create a Pinecone account and get your API key
   * Sign up for SerpAPI for Google Search access
   * Get OpenWeatherMap API key for weather data

4. **Run the script** and enter your API keys when prompted:
```bash
python main.py
```

5. **Interact with the agent** by asking research questions across different domains.

**📋 Example Queries**

**AI Research Query**:
```
What are the latest developments in transformer architecture for large language models?
```

**Mixed Information Query**:
```
Give me news and weather for Chennai today
```

**Specific Paper Analysis**:
```
Explain the methodology used in ArXiv paper 2301.12345
```

**General Knowledge**:
```
How does quantum computing differ from classical computing?
```

**Response Format**: The agent will conduct multi-step research and respond with a structured report including:
- Introduction to the topic
- Research methodology used
- Comprehensive findings
- Professional conclusion
- Detailed source citations
