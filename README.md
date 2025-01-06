# DocumentIQ: File Query Assistant

DocumentIQ is an AI-powered application that enables users to query uploaded PDF documents. It leverages LangChain, OpenAI's GPT model, and Chroma vector stores to create a seamless question-answering system based on document retrieval and contextual understanding.

### Features

- PDF Upload and Processing: Users can upload multiple PDF files for analysis.

- Document Chunking: Uploaded PDFs are split into manageable chunks to optimize document retrieval.

- Vector Database: Stores document embeddings for fast and accurate information retrieval.

- Interactive QA System: Allows users to ask questions and receive precise answers based on the uploaded documents.

- Streaming Responses: Real-time streaming of responses from the LLM.

- Source Tracking: Displays the top three document sources used to generate the LLM's response.

### Requirements

* Python Libraries: Ensure you have the following libraries installed:

  - streamlit

  - langchain

  - pyngrok

  - pandas

  - chromadb

  - PyMuPDF

  - os

  - tempfile

You can install these dependencies using:

`pip install streamlit langchain pyngrok pandas chromadb PyMuPDF`

### How to Run
* Clone the Repository

  - `git clone <repository_url>
  cd <repository_directory>`

* Set Up Ngrok

  - Install Ngrok: https://ngrok.com/download

  - Set your authentication token in the script by replacing `NGROK_TOKEN_API_KEY` with your Ngrok auth token.

* Run the Application

  - Start the Streamlit app by running:

  - streamlit run app.py

- Ngrok will create a public URL to access the app. The URL will be printed in the terminal as: Streamlit App: <Ngrok_URL>

Visit the provided Ngrok URL in your browser to access the application.

### Application Workflow

- Upload Files: Use the file uploader in the sidebar to upload PDF documents.
* Document Processing:

  - Documents are read and split into chunks using RecursiveCharacterTextSplitter.

  - The chunks are embedded using `OpenAIEmbeddings` and stored in a `Chroma` vector database.

- Ask Questions: Enter your question in the chat interface.

* Retrieve and Respond:

  - Relevant document chunks are retrieved from the vector database.

  - The LLM generates an answer based on the retrieved content.

  - Sources used for the response are displayed.

### Key Components

**Functions and Classes**

* `configure_retriever(uploaded_files)`
  -  Reads uploaded PDF documents, splits them into chunks, computes embeddings, and stores them in a Chroma vector database.
  -  Returns a retriever for querying the database.

* `StreamHandler`

  -  Handles streaming updates to the user interface in real-time.

* `PostMessageHandler`

  -  Extracts and displays the top three document sources used in generating the LLM's response.
* **Prompt Template**: The prompt template for the QA system ensures that responses are concise and based solely on the provided context.

### Notes
- Session State Management: The app uses StreamlitChatMessageHistory to maintain conversation history between user and AI.

- Persistence: The vector database is stored in the `./chroma_persist` directory for future use.

- Customizability: Modify the QA prompt template to suit your specific requirements.
