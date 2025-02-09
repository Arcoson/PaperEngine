# PaperEngine API Documentation

## Endpoints

### Aggregate Papers

- **Description**: Aggregates research papers from multiple sources.
- **Method**: GET
- **Parameters**:
  - `query` (string): The search query.
  - `limit` (int): Maximum number of papers to retrieve (default: 10).

### Search Papers

- **Description**: Searches for specific papers across multiple sources.
- **Method**: GET
- **Parameters**:
  - `query` (string): The search query.
  - `source` (string): Filter by source (arxiv, pubmed, semantic_scholar, google_scholar).
  - `year` (int): Filter by publication year.