# 0.1.6
## 06-03-2025
- Added support for using temporary paths
- Changed the database from Chrome_db to FAISS
- Added a new preprocessor (PyMuPDF) to improve text extraction, perform table extraction, and enable potential image extraction via OCR
    > ⚠️ **Warning**: It may still present issues and not function as expected

# 0.1.7
## 06-04-2025
- The system prompt for the bots was changed to make them more conversational.
- Fixed errors in MyPyPDFPreprocessing for environments without Tesseract.
- Fixed path errors in RAG (Retrieval-Augmented Generation).

# 0.1.8 
## 06-05-2025 
- Some errors related to the use of RAG were corrected.

# 0.1.9
## 06-06-2025
- Functionality for interacting with Hugging Face APIs was added.
- The chatbot functionality was modularized to support integration with both Ollama and Hugging Face.
- Errors in the preprocessor were corrected.
- Issues related to the RAG component were fixed.

