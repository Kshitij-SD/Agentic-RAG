# RAG Question Answering System

## Overview
This project implements a Retrieval-Augmented Generation (RAG) system with agentic capabilities, allowing users to upload PDF documents and ask questions about their content. The system intelligently routes queries to appropriate tools (document search, math calculations, or web search) using a custom agent architecture.

## Key Components

### Architecture
1. **Document Processing Pipeline**:
   - PDF loading with PyPDFLoader
   - Text splitting with CharacterTextSplitter
   - Vector embedding using Google's Gemini embeddings
   - FAISS vector store for efficient similarity search

2. **Agent System**:
   - Custom ReAct agent with tool routing
   - Four specialized tools:
     - QueryRouter (determines best tool for each query)
     - RAGQA (document-specific questions)
     - llm-math (mathematical calculations)
     - ddg-search (general knowledge/definitions)

3. **Web Interface**:
   - Flask backend serving API endpoints
   - Bootstrap-based frontend with interactive chat

### Key Design Choices
1. **Tool Routing**: Implemented a QueryRouter tool that analyzes queries first to determine the most appropriate tool, improving efficiency.
2. **Thinking Visualization**: Added detailed logging of the agent's decision-making process for transparency.
3. **Error Handling**: Robust error handling for PDF processing and query execution.
4. **Modular Design**: Separated document processing, agent logic, and web interface for maintainability.

## How to Run

### Prerequisites
- Python 3.8+
- Google API key (set as environment variable `GOOGLE_API_KEY`)
- Required packages: `flask`, `langchain`, `langchain-google-genai`, `faiss-cpu`

### Installation
1. Clone the repository
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Application
1. Start the Flask server:
   ```bash
   python app.py
   ```
2. Open a web browser and navigate to `http://localhost:5000`

### Usage
1. Upload a PDF document using the web interface
2. Once processed, ask questions about the document content
3. The system will show both answers and the agent's reasoning process

## Future Enhancements
- Support for more document types
- Improved query routing logic
- User authentication and document management
- Performance optimizations for large documents
