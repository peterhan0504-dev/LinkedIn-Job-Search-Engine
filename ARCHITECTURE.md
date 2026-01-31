# Architecture

Overview of the system components and data flow.

1. Data collection & preprocessing
   - Source: `datastax/linkedin_job_listings` (Hugging Face dataset)
   - Notebook: `Preprocessing.ipynb`
   - Outputs: `linkedin_jobs_cleaned.sqlite` (table: `job_listings_cleaned`), metadata table

2. Embedding generation
   - Notebook: `semantic.ipynb`
   - Model: `sentence-transformers/all-MiniLM-L6-v2` (384-dim)
   - Outputs: in-memory embeddings (recommend caching to disk/SQLite)

3. Retrieval
   - Approach: cosine similarity on sentence embeddings (top-K)
   - Implementation: `model.similarity()` and post-processing to select top-K

4. LLM QA (RAG)
   - Retrieve top-K descriptions and build a context string
   - Send context + user question to OpenAI chat endpoint
   - Model: `gpt-3.5-turbo` (configured in notebook for broader access)

5. Files & security
   - `.env` stores `OPENAI_API_KEY` (excluded from git via `.gitignore`)
   - `.env.example` included as template

Notes / future work:
- Cache embeddings to avoid repeated encoding.
- Split long descriptions into chunks and rerank retrieved chunks.
- Add a small API/service layer to serve retrieval + QA.
