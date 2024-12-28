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

Libraries/Modules imported: 
1. output_parsers, prompts from langchain_core
2. ChatOpenAI from langchain_openai
3. Ollama from langchain_community.llms: to run LLM on local servers aka. #DockerForLLMs supports various libraries such as LLama2, Claude, Mistral, Dolphin Phi, and LLaVa (cmd: "ollama run modelname")
# Other Useful Frameworks, Libraries, Tools:
 <ol>
  <li>Ollama: (Omni-Layer Learning Language Acquisition Model)
      <p> </p> </li>
  <li>Streamlit: to turn DS, ML apps into web applications (cmd: "streamlit run filename.py") </li>
  <li>Fast API: to perform production-grade deployment of LLM as API. Perform Swagger UI Documentation.</li>
  <li>Uvicorn: an Asynchronous Server Gateway Interface (ASGI) Server which acts as binding element that handles web connections from browser or api client and then allows FastAPI to serve actual request (cmd: uvicorn.run())  </li>
 </ol>

 # RAG Pipeline using LangChain Chromadb and FAISS
![RAG](https://github.com/user-attachments/assets/5ead9382-0ec4-40d8-bc4f-a512b7572b62)

Libraries/Modules imported: 
1. langchain_community.document_loaders -> to load text, pdf, web documents.
2. bs4 -> to extract data from HTML, XML files(web scraping).
3. langchain.text_splitter -> to split into chunks.
4. langchain_community.vectorstores -> Chroma (ease of use, versatile, full-featured db capabilities), FAISS (large-scale, high performance, GPU-accelerated)
5. OpenAIEmbeddings from langchain_openai : converts text into numerical vectors for tasks like similarity search, clustering, NLP
