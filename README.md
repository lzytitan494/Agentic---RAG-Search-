# Agentic-RAG-with-Search
This repository contains an implementation of an adaptive Retrieval-Augmented Generation (RAG) system using LangChain and Cohere APIs. The system intelligently routes user questions to either a vector store containing pre-indexed documents or performs a web search based on the nature of the question. It leverages a series of prompts and models to ensure the generation is accurate and relevant.
## Features
### Environment Setup:

* Set user agent and API keys for Cohere and Tavily services.
### Indexing:

* Load documents from specified URLs.
* Split the documents into manageable chunks.
* Store the chunks in a Chroma vector store with Cohere embeddings.
### Question Routing:

* Route user questions to either the vector store or web search or None (model will directly answer)
* Use few-shot prompting to train the model on routing decisions.
### Retrieval and Generation:

* Retrieve relevant documents from the vector store.
* Generate answers using the retrieved documents or fallback to the LLM if necessary.
* Grade the relevance of retrieved documents and the generated answers.
### Grading and Quality Control:

* Grade the relevance of documents and generated answers.
* Ensure the generated answers are grounded in the retrieved documents to prevent hallucinations.
* Re-write and optimize questions for better retrieval if initial results are unsatisfactory.
### Graph Workflow:

* Define a workflow using a state graph to manage the entire process, from question routing to answer generation and grading.

## Usage
The system can be run with different input questions to demonstrate its capabilities. The workflow adapts based on the input question, performing retrieval, generation, grading, and re-writing as needed.

```
inputs = {
    "question": "What are the types of different graph neural nets?"
}
for output in app.stream(inputs):
    for key, value in output.items():
        print(f"Node '{key}':")
    print("\n---\n")
    time.sleep(6)
    print("\n---\n")

print(value["generation"])
```
