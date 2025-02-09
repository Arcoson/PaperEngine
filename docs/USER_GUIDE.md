# PaperEngine User Guide

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/arcoson/PaperEngine.git
   pip install -r requirements.txt
   python src/cli.py aggregate --query "machine learning" --limit 5

# Usage 

## Aggregate Papers

```bash
python src/cli.py aggregate --query "quantum computing" --limit 10
```

## Search Papers

```bash
python src/cli.py search --query "neural networks" --source arxiv --year 2022
```

## Configuration

You can configure default settings in `src/config/settings.py` or modify user preferences in `src/config/preferences.json`.


