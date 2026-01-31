# NLP Project - Notebooks and Usage
## LLM Enhancement

This project uses an LLM to **answer user questions based on the retrieved top-K job descriptions** (Option B in the project rubric).

The retrieved job descriptions are concatenated into a context window and passed to the LLM along with the user query to generate a grounded response.


# Semantic Search Engine for LinkedIn Job Listings

This project implements a production-ready **semantic search engine** over LinkedIn job postings using **sentence embeddings** and **cosine similarity**, with optional **LLM-based question answering**.

**Domain:** Jobs / Job Listings  
**Data:** LinkedIn job postings (100k+ records)  
**Core techniques:** Sentence Transformers, vector similarity search, SQLite, LLM-based QA

Users can query natural-language job intents (e.g. *"entry level data analyst"*) and retrieve the most semantically relevant job descriptions.
## Data

Due to GitHub repository file size limits, the full SQLite database (~450MB) is **not tracked in git**.

### Download the database
Download `linkedin_jobs_cleaned.sqlite` from the GitHub Release:
https://github.com/peterhan0504-dev/Semantic-Search-Engine/releases/tag/v1.0-data

### Usage
After downloading, place the file in the project root directory before running the CLI.

## Files
- [Preprocessing.ipynb](Preprocessing.ipynb) - data cleaning and preprocessing steps.
- [semantic.ipynb](semantic.ipynb) - loads a SQLite dataset, computes sentence embeddings with `all-MiniLM-L6-v2`, and computes similarities.
- [requirements.txt](requirements.txt) - Python dependencies.

## Prerequisites
- Python 3.8+ (use the system `python3` if needed)

## Command Line Interface (CLI)

The project includes a command-line interface for running semantic search over the job database.

### Example
```bash
python cli.py "entry level data analyst" --k 5


## Quick setup
Run these commands from the workspace root in a terminal:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

If `python3` is not available, replace with your Python binary.

## Notes for `semantic.ipynb`
- The notebook opens a SQLite database via a `db_path` variable. Update that path to point to your local copy of `linkedin_jobs_cleaned.sqlite` if needed.
- The notebook uses the `SentenceTransformer("all-MiniLM-L6-v2")` model (embedding size = 384).
- Cells already encode the first N descriptions and compute similarity; adjust the slice (`head(50)` or similar) to change the number of sentences.

## OpenAI API Key Setup (for LLM-based QA)
The `semantic.ipynb` notebook includes a question-answering feature that requires an OpenAI API key.

**Secure Setup:**
1. Copy `.env.example` to `.env`:
   ```bash
   cp .env.example .env
   ```
2. Add your OpenAI API key to `.env`:
   ```
   OPENAI_API_KEY=sk-your-actual-key-here
   ```
3. The `.env` file is in `.gitignore` and will NOT be committed to Git (safe!).
4. The notebook will automatically load your key from `.env` when you run it.

**Get your API key:**
- Visit [platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys)
- Create a new API key and copy it to your `.env` file

## How to run
1. Activate the virtual environment (see Quick setup).
2. Open the notebooks in Jupyter or VS Code and run cells in order.

## Next steps / Handoff
- If you need me to run the notebooks, install the environment, or export embeddings, tell me which notebook and I will run it.
- If you move the database, update the `db_path` variable in `semantic.ipynb`.

---
If anything is unclear, ping me or leave a short note in the repo and I will follow up.
