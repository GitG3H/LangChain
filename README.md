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
1. langchain_community.document_loaders -> to load text, pdf, web documents. (TextLoader, WebBaseLoader, PyPDFLoader) (function: loader.load())
2. bs4 -> to extract data from HTML, XML files(web scraping).
3. langchain.text_splitter -> to split into chunks. (RecursiveCharacterTextSplitter(), RCTS.split_documents())
4. langchain_community.vectorstores -> Chroma (ease of use, versatile, full-featured db capabilities),
                                    -> FAISS by Meta (large-scale, high performance, GPU-accelerated) (FAISS.from_documents(docs,embeddings))
6. langchain_community.embeddings -> OpenAIEmbeddings (advanced, better performance)/OllamaEmbeddings : converts text into numerical vectors for tasks like similarity search, clustering, NLP. 

# Advanced RAG Q&A Chatbot with Chain and Retrievers using LangChain.

Chain: Sequence of calls (automated actions) that link AI components to provide context-aware responses.
Reasons to use chains: 
1. Break down complex tasks and handle them sequentially.
2. Add state and memory (Output of one call is fed as input to next call to provide context)
3. Add processing logic between calls (Eg: Additional processing, filtering, validation)
4. Debug and instrument.
Useful chains: create_stuff_documents_chain, create_retrieval_chain, create_sql_query_chain

Retriever: An interface that returns documents given an unstructured query. (cmd: db.as_retriever())
Retrieval Chain: This chain takes user inquiry, which is then passed to retriever to fetch relevant documents. (cmd: create_retrieval_chain(), invoke())

![Retriever_Chain_LCEL](https://github.com/user-attachments/assets/8f2f9dfa-fec8-4c30-9105-645a140cf2aa)

Libraries/Modules imported:
1. langchain.chains.combine_documents -> create_stuff_documents_chain
2. langchain.chains-> create_retrieval_chain
3. Other: OS, Ollama, prompts, chat_models, streamlit, requests.

# Advanced RAG Q&A with multiple data sources with LangChain
1. Tools: Interfaces that an agent, chain, or LLM can use to interact with the world. E.g. ArXiv, AWS Lambda, Bing Search, ChatGPT Plugins, Google Lens etc.
   They are wrapped in toolkit.
2. Agent: an AI system that uses LLM to control an application's flow & interact with tools to perform tasks or answer questions.
3. AgentExecutor: Runtime for an agent that calls the agent, execute actions it chooses, passes action outputs back to agent and repeats. i.e. it implements standard Runnable interface  
4. LangChain Hub: an extension from LangSmith Studio environment that lets you discover, share and version control prompts which are listed publicly.

Libraries/Modules imported:
1. langchain_community.tools -> WikipediaQueryRun, ArxivQueryRun
2. langchain_community.utilities -> WikipediaAPIWrapper, ArxivAPIWrapper
3. langchain.tools.retriever -> create_retriever_tool()
4. langchain.agents -> create_openai_tools_agent(llm model to use, sequence of tools, prompt), AgentExecutor.invoke({"input"})
5. langchain.hub -> hub.pull()  (all publicly listed prompts are available in hub)
6. Other: OpenAIEmbeddings, WebBaseLoader, RecursiveCharacterTextSplitter, FAISS

# E2E Advanced RAG project using Open Source LLM models and Groq Inferencing Engine
1. Groq LPU Inference Engine: Groq is an AI Inference company. It uses LPU (Language Processing Unit) that overcomes 2 LLM bottlenecks (Compute density, memory bandwidth).

Libraries/Modules imported:
1. langchain_groq -> ChatGroq 
2. langchain_core.prompts -> ChatPromptTemplate
3. Other: streamlit, os, WebBaseLoader, OllamaEmbeddings, RecursiveCharacterTextSplitter, create_stuff_documents_chain, create_retrieval_chain, FAISS, time

Steps:
1) Load Groq API Key
2) Define/Set Configurations for Streamlit Session State Variables.         st.session_state.(embeddings, loader, docs,text_splitter, final_documents,vectors)
3) Set title for Streamlit app
4) Define llm and pass parameters (llm=ChatGroq(groq_api_key, model_name))
5) Define base prompt and provide placeholders for context and input so that user can type these in UI.
6) Create a document_chain(llm,prompt) and retriever then pass them into retrieval_chain.
7) Additionally you can capture the process_time to check how much time the model is taking to retreive the info.
   
# Gen AI powered app using LangChain + HuggingFace + Mistral

Libraries/Modules imported: 
1) langchain_community.embeddings -> HuggingFaceBgeEmbeddings
2) langchain.chains -> RetrievalQA
3) langchain_community.llms -> HuggingFaceHub
4)Other: PyPDFLoader, PyPDFDirectoryLoader, RecursiveCharacterTextSplitter, FAISS, numpy, PromptTemplate,

Steps: 
1) Read pdfs from loader and split the documents. (loader.load(), RCTS(), split_documents())
2) Specify parameters for Huggingface_embeddings. (model_name, kwargs)
3) Embed page content of first document to hugging face embeddings and convert to array (.embed_query(), np.array().shape)
4) Creates a FAISS vector store from first few documents of final_documents using huggingface_embeddings. (FAISS.from_documents())
5) Provide a query and fetch content from relevant documents using similarity_search, then use as_retriever
6) Call required models from hugging face hub, provide a query and invoke it. (hf.invoke(query))
   Note: to run models locally use HFPipeline instead of HFHub.
7) Create a prompt with prompt template (context, question) and invoke it.

9) 
