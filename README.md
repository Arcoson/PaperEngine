# PaperEngine

**PaperEngine** is a powerful command-line tool designed to aggregate and search research papers from multiple sources, including **Arxiv**, **PubMed**, and **Semantic Scholar**. (Google Scholar is temporarily disabled but can be re-enabled easily.)

With its intuitive interface and advanced features, PaperEngine makes it easy to discover, filter, and save academic papers for your research needs.

---

## Table of Contents
1. [Features](#features)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Configuration](#configuration)
5. [Database](#database)
6. [Contributing](#contributing)
7. [License](#license)

---

## Features
- **Multi-Source Aggregation**: Fetch papers from Arxiv, PubMed, and Semantic Scholar.
- **Advanced Search**: Filter results by source, publication year, and author.
- **Persistent Storage**: Save aggregated papers to an SQLite database for future reference.
- **Beautiful CLI Interface**: Colorful and user-friendly output powered by the `rich` library.
- **Customizable Preferences**: Configure default settings via `preferences.json`.

---

## Installation

### Prerequisites
- Python 3.8 or higher
- `pip` (Python package manager)

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/arcoson/PaperEngine.git
   cd PaperEngine
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up environment variables:
   - Create a `.env` file in the root directory and add any required API keys:
     ```env
     ARXIV_API_KEY=  # Not required
     PUBMED_API_KEY=your_pubmed_api_key # only if >100 requests (check with pubmed)
     SEMANTIC_SCHOLAR_API_KEY=  # Not required
     GOOGLE_SCHOLAR_API_KEY=  # Temporarily disabled
     DATABASE_PATH=papers.db
     ```

---

## Usage

### Aggregate Papers
Aggregate papers from multiple sources based on a query:
```bash
python src/cli.py aggregate --query "machine learning" --limit 10
```

### Search Papers
Search for specific papers with optional filters:
```bash
python src/cli.py search --query "neural networks" --source arxiv --year 2022
```

### View Saved Papers
All fetched papers are saved to an SQLite database (`papers.db`). You can view them using the SQLite CLI:
```bash
sqlite3 papers.db "SELECT * FROM papers;"
```

---

## Configuration

You can customize the behavior of PaperEngine by modifying the following files:

- **`src/config/preferences.json`**: User preferences such as default query limits and themes.
- **`.env`**: Environment variables for API keys and database paths.

Example `preferences.json`:
```json
{
    "default_query_limit": 10,
    "default_source": "arxiv",
    "default_year_filter": null,
    "theme": "dark",
    "show_advanced_options": false
}
```

---

## Database

PaperEngine uses an SQLite database (`papers.db`) to store fetched papers. The database schema includes the following fields:
- `title`: Title of the paper.
- `authors`: Comma-separated list of authors.
- `published_date`: Publication date of the paper.
- `source`: Source of the paper (e.g., Arxiv, PubMed).

You can query the database directly using SQLite commands or integrate it into other tools.

---

## Contributing

We welcome contributions to improve PaperEngine! Here's how you can help:
1. Fork the repository and create a new branch.
2. Make your changes and ensure all tests pass:
   ```bash
   pytest src/tests/
   ```
3. Submit a pull request with a detailed description of your changes.

For major changes, please open an issue first to discuss your ideas.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Inspired by best practices for README files [[1]].
- Built using Python libraries like `requests`, `rich`, and `lxml`.
- Thanks to the open-source community for providing tools and APIs that power this project.

---

## Notes

- **Google Scholar**: Temporarily disabled due to potential scraping issues. To re-enable it, uncomment the relevant lines in `src/aggregator/core.py`:
  ```python
  # google_scholar_papers = google_scholar_client.fetch_papers(query, limit)
  google_scholar_papers = google_scholar_client.fetch_papers(query, limit) # this might not work as google scholar does not have offical API, might need to implement web scraping
  ```
