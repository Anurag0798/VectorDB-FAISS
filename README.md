# VectorDB-FAISS

This repository demonstrates how to build a vector search system using **FAISS** and embeddings generated via the **Euron API**. It covers the full pipeline from preparing unstructured text data to performing similarity search with FAISS.

## Setup and Installation

To get started, install FAISS using pip:

```bash
pip install faiss-cpu
```

Make sure you have other dependencies installed as needed for API calls and data processing (e.g., `numpy`, `requests`).

## Data Preparation

- **Why embeddings?**
  Unstructured text data must be converted into numerical embeddings to enable similarity search.

- **Chunking Text Data:**
  Large documents are split into smaller chunks for better search granularity and performance.

- **Chunk Size and Overlap:**
  - Chunks are sized to balance detail and efficiency.
  - Overlapping chunks help maintain context between pieces, improving search relevance.

## Embedding Generation

- **Using the Euron API:**
  Text chunks are sent to the Euron API to generate embeddings.

- **API Details:**
  - **API URL:** Your Euron API endpoint
  - **API Key:** Required for authentication
  - **Model:** `text embedding-3-small` is used for embedding generation

- **Data Conversion:**
  Embeddings returned by the API are converted into a `float32` NumPy matrix to be compatible with FAISS.

## FAISS Implementation

- **Creating an Index:**
  Use `faiss.IndexFlatL2` which performs similarity search based on Euclidean distance.

- **Adding Embeddings:**
  The generated embeddings are added to the FAISS index.

- **Persisting the Index:**
  The index is saved to disk using `faiss.write_index` for later reuse.

## Similarity Search

- **Query Processing:**
  Input query text is converted into an embedding using the Euron API.

- **Searching FAISS:**
  The query embedding is searched against the FAISS index to find the most similar stored embeddings.

- **Parameters:**
  - `top_k` controls how many closest matches are returned.

## Key Takeaways

- Vector databases are essential for performing similarity search and enabling Retrieval-Augmented Generation (RAG) applications.

- FAISS is a powerful and efficient tool for building vector search engines.

- Proper text data preparation (chunking and overlap) and embedding generation directly impact search accuracy.

- The Euron API offers a convenient and effective way to generate embeddings suitable for FAISS.

## Getting Started

1. Prepare your unstructured text data and split it into chunks with appropriate overlap.

2. Generate embeddings for each chunk using the Euron API.

3. Create a FAISS index (`IndexFlatL2`) and add the embeddings.

4. Save the index for future use.

5. To perform a similarity search, embed the query text and use the FAISS index's `search` method to find the closest chunks.

## License

This project is open-source. See the `LICENSE` file for details.
