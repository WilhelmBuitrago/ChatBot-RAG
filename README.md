# ChatBot-RAG

A powerful chatbot implementation using Retrieval Augmented Generation (RAG) to provide context-aware responses based on your data.

## Features

- 🔍 **Retrieval Augmented Generation**: Enhances LLM responses with relevant context from your data
- 🧠 **Ollama Support**: Run models locally with Ollama for privacy and customization
- 🔗 **LangChain Integration**: Built on the powerful LangChain framework for advanced chains and pipelines

## Installation

```bash
pip install chatbot-rag
```

## Requirements

- Python 3.12
- Ollama (for local model hosting)
- Tesseract-OCR (for image-based data extraction)

### Tesseract Installation

To enable image-based data extraction, you need to install **Tesseract-OCR**.  
Follow the installation instructions provided at this [link](https://tesseract-ocr.github.io/tessdoc/Installation.html).

After installation, ensure the `tesseract` executable is accessible in your system's PATH.  
For example, on Windows, you can verify by running:

```bash
tesseract --version
```

### Ollama Installation

Ollama is required for hosting models locally.  
Refer to the official Ollama documentation for installation instructions: [Ollama Installation Guide](https://ollama.com/docs/installation).

Once installed, verify it is working by running:

```bash
ollama --version
```

## Use

### Quick Start
```python
from chatbot_rag.chat import Chatbot 
from chatbot_rag.RAG import RAG

# Use a specific Ollama model
rag = RAG(path="./data/")
rag()
bot = Chatbot(name="deepseek-r1:8b")

# Query with specific parameters
question = "Summarize my recent research on climate change"
context  = rag._search_context(question,k=5)
response = bot(context,question)
print(response)
```

### Using temporal paths
```python
from chatbot_rag.chat import Chatbot 
from chatbot_rag.RAG import RAG


with tempfile.TemporaryDirectory() as tmpdirname:
    persistent_dir = os.path.join(tmpdirname, "all_info/")
    os.makedirs(persistent_dir, exist_ok=True)
    rag = RAG(path="./data/",base_persist_path=persistent_dir)
    rag()
    chatbot = Chatbot(name="llama3.1:8b")

    question = "What is the main topic of the document?"
    context = rag._search_context(question)
    answer = chatbot(context=context, question=question)
    print(f"Answer: {answer}")
```

### Using other preprocessing (PyMuPDFPreprocessing)


```python
from chatbot_rag.chat import Chatbot 
from chatbot_rag.RAG import RAG
from src.chatbot_rag.preprocessing import PyMuPDFPreprocessing


kwargs = {"tesseract_path": "C:/Program Files/Tesseract-OCR/tesseract"}
rag = RAG(path="./data/",preprocessing=PyMuPDFPreprocessing,**kwargs)
rag()
chatbot = Chatbot(name="llama3.1:8b")

question = "What is the main topic of the document?"
context = rag._search_context(question)
answer = chatbot(context=context, question=question)
print(f"Question: {answer}")
```


By default, the system will attempt to extract information from images using **Tesseract-OCR**. You can disable image extraction by adding the following to the `kwargs`:

```python
kwargs = {"extract_images": False}
```

and passing it directly to the RAG component.

## Projects Using ChatBot-RAG

### 🌟 [ChatBot-RAG App](https://github.com/WilhelmBuitrago/chatbot_rag_app)

ChatBot-RAG App is a chatbot framework leveraging **Retrieval-Augmented Generation (RAG)** to deliver context-aware responses.  
It integrates **🔗 LangChain** for advanced pipelines and supports **🧠 Ollama** for local model hosting, ensuring enhanced privacy and customization.

Key Features:
- 🔍 **Context-Aware Responses**: Uses RAG to provide accurate and relevant answers.
- 🧠 **Local Model Hosting**: Powered by Ollama for privacy and flexibility.
- 🔗 **Advanced Pipelines**: Built on LangChain for seamless integration and extensibility.

Explore the project here: [ChatBot-RAG App](https://github.com/WilhelmBuitrago/chatbot_rag_app)

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details.
