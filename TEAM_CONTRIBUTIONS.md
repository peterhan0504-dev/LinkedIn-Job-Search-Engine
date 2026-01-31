# Team Contributions

This file documents who contributed what for the deliverable.

Contributors:


- Shuaiyu Yao:
  - **Domain Selection:** Researched and proposed the job listings domain (LinkedIn jobs) and obtained instructor approval; identified `datastax/linkedin_job_listings` as the corpus source.
  - **Data Collection:** Collected and curated the raw dataset; verified dataset size (>100 documents), sampled records for quality checks, and coordinated placement of the `linkedin_jobs_cleaned.sqlite` file in the project workspace.
  - **Embedding Implementation:** Selected `sentence-transformers/all-MiniLM-L6-v2`, assisted in embedding generation workflow, validated embedding dimensions and similarity computations, and helped test retrieval/top-K logic in `semantic.ipynb`.

- Anwen_Ann_Chen:
   - **LLM Enhancement:** Implemented the RAG-based QA pipeline in `semantic.ipynb` (retrieval, context assembly, prompt engineering and OpenAI integration) and tested example queries.
  - **Project files:** Added `ARCHITECTURE.md` and `TEAM_CONTRIBUTIONS.md` to document the project structure and contributions.

- Hongde Han
  - **Interface / Deployment:** Implemented command-line deployment scripts and explored deployment options (Streamlit, Gradio, and Hugging Face Spaces) for a publicly accessible demo; prepared deployment notes and example commands.
  - **Code Quality:** Ensured code is modular and documented, added error handling improvements, and verified `requirements.txt` covers runtime dependencies.

 Assistant (GitHub Copilot):
  - Implemented embedding + retrieval pipeline in `semantic.ipynb`.
  - Helped debug environment, installed dependencies, and configured notebook kernel.

 
