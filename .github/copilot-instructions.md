# Copilot Instructions for book-homl

## Project Overview
- This repo is for learning and experimenting with the "Hands-On Machine Learning" book by Aurélien Géron.
- Code is organized by chapter, with each chapter in its own subdirectory (e.g., `chapter-02/`).
- Each chapter may contain Jupyter notebooks, data files, and supporting scripts.

## Key Patterns & Conventions
- Jupyter notebooks are the primary format for code and exploration.
- Data files are stored under `chapter-XX/data/`.
- Notebooks often include data acquisition, exploration, visualization, and modeling in a single file.
- Use public APIs for type annotations (e.g., `pd.DataFrame` not internal classes).
- Follow the book's structure and naming conventions for files and functions.

## Developer Workflows
- No custom build or test scripts; run and experiment directly in Jupyter.
- To run code, open the relevant notebook in VS Code or JupyterLab and execute cells sequentially.
- Data is downloaded automatically by notebook code if not present.
- No CI/CD or automation is set up; this is a learning sandbox.

## External Dependencies
- Main dependencies: pandas, numpy, matplotlib, scikit-learn (as used in the book).
- Install dependencies via pip or conda as needed; requirements are not strictly enforced.
- Notebooks may download datasets from the web (see code for URLs).

## Example: Data Loading Pattern
```python
from pathlib import Path
import pandas as pd
import tarfile
import urllib.request

def fetch_load_data() -> pd.DataFrame:
    tarball_path = Path("data/housing_data.tgz")
    if not tarball_path.is_file():
        urllib.request.urlretrieve(HOUSING_DATA_URL, tarball_path)
    with tarfile.open(tarball_path) as data_tarball:
        data_tarball.extractall(path=Path("data/"))
    return pd.read_csv(Path("data/housing/housing.csv"))
```

## Guidance for AI Agents
- Prioritize clarity and reproducibility in code and explanations.
- When adding new notebooks, follow the chapter-based directory structure.
- Use inline comments to explain non-obvious steps, especially data wrangling and modeling logic.
- Avoid introducing complex build systems or automation unless explicitly requested.
- Reference the book for context and rationale behind code patterns.
