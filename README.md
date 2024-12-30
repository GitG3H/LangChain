# LangChain
framework for developing apps powered by LLMs

# **LangChain Ecosystem:**
 >    1. **LangSmith**: for observability
 >    2. **LangServe**: for deploying chains as APIs
 >    3. **Templates**: Reference Applications
 >    4. **LangChain: Chain / Agents / Advanced Retrieval Strategies**
 >    5. **LangChain Community**: Integrations/Components
                    Models I/O
                    Retrieval
                    Agent Tooling
 >    6. **LangChain Core**: Protocol
                    LCEL - LangChain Expression Language

 # Building Chatbot using paid & open source LLMs using LangChain and Ollama
 Libraries/Modules imported: 
1. output_parsers, prompts from langchain_core and ChatOpenAI from langchain_openai
2. Ollama from langchain_community.llms: to run LLM on local servers aka. #DockerForLLMs supports various libraries such as LLama2, Claude, Mistral, Dolphin Phi, and LLaVa (cmd: "ollama run modelname")
3. Streamlit: to turn DS, ML apps into web applications (cmd: "streamlit run filename.py")

 # Production-grade deployment of LLM as API with Langchain and FastAPI
1. Fast API: to deploy LLM as API. Perform Swagger UI Documentation.
2. Uvicorn: ASGI Server -> a binding element that handles web connections from browser or api client and then allows FastAPI to serve actual request. (cmd: uvicorn.run())
   -WSGI (Gunicorn) is synchronous i.e. requests handled one at a time. (suitable for traditional web apps). suitable for Flask, Django
   -ASGI (Uvicorn) is asynchronous i.e. utilize async/await syntax, async I/O to handle more reqs simultaneously. (use: real time appns). suitable for FastAPI, Starlette    
3. add_routes from LangServe: to deploy LangChain runnables and chains as REST API
4. Other: OS, Ollama, prompts, chat_models, streamlit, requests.

 # RAG Pipeline using LangChain Chromadb and FAISS vector databases.
![RAG](https://github.com/user-attachments/assets/5ead9382-0ec4-40d8-bc4f-a512b7572b62)
Libraries/Modules imported: 
1. langchain_community.document_loaders -> to load text, pdf, web documents.
2. bs4 -> to extract data from HTML, XML files(web scraping).
3. langchain.text_splitter -> to split into chunks.
4. langchain_community.vectorstores -> Chroma (ease of use, versatile, full-featured db capabilities), FAISS by Meta (large-scale, high performance, GPU-accelerated)
5. langchain_community.embeddings -> OpenAIEmbeddings (advanced, better performance)/OllamaEmbeddings : converts text into numerical vectors for tasks like similarity search, clustering, NLP. 

# Advanced RAG Q&A Chatbot with Chain and Retrievers using LangChain.

Chain: Sequence of calls (automated actions) that link AI components to provide context-aware responses.
Reasons to use chains: 
1. Break down complex tasks and handle them sequentially.
2. Add state and memory (Output of one call is fed as input to next call to provide context)
3. Add processing logic between calls (Eg: Additional processing, filtering, validation)
4. Debug and instrument.
![Retriever_Chain_LCEL](https://github.com/user-attachments/assets/8f2f9dfa-fec8-4c30-9105-645a140cf2aa)

Useful chains: create_stuff_documents_chain, create_retrieval_chain, create_sql_query_chain

Retriever: An interface that returns documents given an unstructured query. (cmd: db.as_retriever())
Retrieval Chain: This chain takes user inquiry, which is then passed to retriever to fetch relevant documents. (cmd: create_retrieval_chain(), invoke())

Libraries/Modules imported:
1. langchain.chains.combine_documents -> create_stuff_documents_chain, 
2. langchain.chains-> create_retrieval_chain
3. Other: OS, Ollama, prompts, chat_models, streamlit, requests.
