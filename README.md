# Elasticsearch Reddit Chat Demo

A demonstration project showing how to process, ingest, and analyse chatroom-style data in Elasticsearch and Kibana for investigative purposes.

## Overview

This project demonstrates how to:

- Ingest semi-structured chat data into Elasticsearch
- Create appropriate index mappings and ingest pipelines
- Build analytics dashboards in Kibana

The demo serves as a practical example for investigators, analysts, and data scientists working with chat room data.

## Project Structure

```bash
es-reddit-chat-demo/
├── data/                        # not included in repo
│   └── reddit/                  # example semi-structured data
│
├── elasticsearch/
│   ├── indices/                 # Index mapping definitions
│   ├── pipelines/               # Ingest pipeline configurations
│   └── dashboards/              # Exported Kibana dashboards
│
├── notebooks/                   # Jupyter notebooks
│   └── ingest_data_elasticsearch.ipynb  # Data ingestion into Elasticsearch
│
├── README.md                    # This documentation
├── requirements.txt             # Python dependencies
├── pyproject.toml               # Project dependencies and configuration
└── uv.lock                      # Dependency lock file for uv
```

## Getting Started

### Prerequisites

- Python 3.12+
- [uv](https://github.com/astral-sh/uv) for Python package management - optional for an easier life
  - `requirements.txt` provided if you would rather roll with pip
- An Elastic Cloud deployment
  - or, a self-hosted Elasticsearch cluster
    - Elasticsearch 8.x+
    - Kibana 8.x+

### Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/face0b1101/es-reddit-chat-demo.git
   cd es-reddit-chat-demo
   ```

2. Create a Python virtual environment and install dependencies:

   ```bash
   uv venv
   uv sync
   ```

3. Start Jupyter Lab to run the notebooks:

   ```bash
   uv run --with jupyter jupyter lab
   ```

## Elasticsearch Resources

### Index Definitions

The `/elasticsearch/indices/` directory contains the index definitions that structure the conversation data in Elasticsearch, ensuring proper field types and search capabilities.

### Ingest Pipelines

The `/elasticsearch/pipelines/` directory contains ingest pipeline definitions that enrich and transform the data during ingestion.

### Dashboards

The `/elasticsearch/dashboards/` directory contains exported Kibana dashboards for visualisation and analysis of the conversation data.
Use the Kibana saved objects UI to import `es-reddit-chat-demo-dashboard.ndjson`. The file contains a saved search, a dashboard and data view. This repo does not cover the [Kibana Saved Objects API](https://www.elastic.co/docs/api/doc/kibana/group/endpoint-saved-objects) at this time.

## License

This project is licensed under the MIT terms, as detailed in the [LICENSE](LICENSE) file.
