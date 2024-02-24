# LLM-to-Chat-with-Multiple-PDF-s
End to End AI Project to Chat With Multiple PDF Documents using Langchain, Google Gemini Pro, and Streamlit.

Streamlit web app to chat with PDFs: https://rag-to-chat-with-pdfs-pebup6bxo7kpx2bzdfajnq.streamlit.app/

This code is a Streamlit web application designed to interactively analyze and answer questions based on text extracted from PDF files using Google Generative AI (Gemini) and a conversational question-answering model.

**Code step by step:**

1. **Imports**: 
    - `streamlit`: Library for creating interactive web applications.
    - `PdfReader`: From PyPDF2 library, used to read PDF files.
    - `RecursiveCharacterTextSplitter`: A class from `langchain.text_splitter` module, used to split text into smaller chunks.
    - `GoogleGenerativeAIEmbeddings`: A class from `langchain_google_genai` module, used to generate embeddings for text.
    - `genai`: Google's Generative AI library.
    - `FAISS`: Vector store for managing embeddings.
    - `ChatGoogleGenerativeAI`: A class from `langchain_google_genai` for conversational interactions with Google's Generative AI.
    - `load_qa_chain`, `PromptTemplate`: Functions and classes for loading a conversational question-answering model and defining prompts.
    - `load_dotenv`: Function to load environment variables from a .env file.

2. **Environment Setup**:
    - `load_dotenv()`: Loads environment variables from a .env file, which presumably contains the Google API key.
    - `os.getenv("GOOGLE_API_KEY")`: Retrieves the Google API key from the environment variables.
    - `genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))`: Configures Google Generative AI with the API key.

3. **Function Definitions**:
    - `get_pdf_text(pdf_docs)`: Reads text from PDF files and returns concatenated text.
    - `get_text_chunks(text)`: Splits input text into smaller chunks.
    - `get_vector_store(text_chunks)`: Generates embeddings for text chunks and creates a vector store using FAISS.
    - `get_conversational_chain()`: Sets up a conversational question-answering chain using a defined prompt and Google's Generative AI model.
    - `user_input(user_question)`: Retrieves embeddings from the vector store, performs similarity search, and uses the conversational chain to generate a response to the user's question.

4. **Main Function**:
    - `main()`: Sets up the Streamlit web application.
        - Sets page configuration and header.
        - Provides a text input field for users to ask questions.
        - Handles user input, including processing PDF files uploaded by the user, extracting text, generating embeddings, and responding to user questions using the conversational chain.
        - Displays a sidebar menu for uploading PDF files and processing them.
        
5. **Execution**:
    - `if __name__ == "__main__": main()`: Executes the `main()` function if the script is run directly.
