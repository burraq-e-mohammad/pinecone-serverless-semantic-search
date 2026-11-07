# Enterprise Vector Search & Semantic Retrieval Pipeline with Pinecone

An end-to-end vector indexing and semantic retrieval pipeline built with **Pinecone Serverless Vector Database** and dense embeddings (`SentenceTransformers` `all-MiniLM-L6-v2`).

## Key Features
- **Multi-Attribute Weighted Embeddings:** Differential weighting for Course Title (5x), Section Name (3x), Description (2x), and Technology (1x) for high-precision semantic matching.
- **Pinecone Serverless Indexing:** Cloud-native vector indexing on AWS `us-east-1` with cosine similarity, dense vector storage (384-d), and batch upserting.
- **Rich Metadata Payloads:** Direct metadata storage in Pinecone enabling instant contextual retrieval and attribute filtering without secondary database lookups.
- **Dual-Level Hierarchical Search:** Fine-grained section search in the default namespace, and composite course discovery in the `courses` namespace.
- **Score Threshold Filtering:** Confidence-calibrated cosine similarity thresholds to isolate relevant results and filter noise.

## Pipeline Architecture
1. **Data Preprocessing & Ingestion:** Ingest curriculum data from `course_section_descriptions.csv` and construct unique identifiers.
2. **Feature Engineering & Embedding:** Compute weighted composite vector representations across titles, sections, and descriptions.
3. **Cloud Vector Indexing:** Upsert section vectors and course composite vectors with payload attributes into Pinecone.
4. **Interactive Retrieval:** Execute semantic vector queries with real-time score filtering and formatted result inspection.

## Quick Start
```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Configure environment credentials
cp .env.example .env
# Set your PINECONE_API_KEY in .env

# 3. Launch notebook
jupyter lab Pinecone_Vector_Search_and_RAG_Pipeline.ipynb
```
