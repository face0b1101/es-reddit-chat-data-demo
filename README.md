# Elasticsearch Reddit Chat Demo

A demonstration project showing how to process, ingest, and analyse chatroom-style data in Elasticsearch and Kibana for investigative purposes.

## Overview

This project provides demo assets for:

- Ingesting semi-structured chat data into Elasticsearch
- Creating appropriate index mappings and ingest pipelines
- Analytics dashboards in Kibana

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

## Setup

### Semantic Search

Make sure you have an Elser inference endpoint deployed in your cluster, and the correct inference ID is used in the `demo-chatroom.data-reddit.json` mappings.

### Named Entity Recognition (NER)

Make sure you have deployed your NER model of choice into your Elasticsearch Cluster. I used `conll03_english_ner`, but other models are available. See [this example](https://www.elastic.co/blog/how-to-deploy-nlp-named-entity-recognition-ner-example) from Elastic on how to deploy NER models into your cluster.

## What does this demo do?

### The Jupyter Notebook

The python notebook provides code to create an index for the reddit chat data with all the mappings needed, along with the ingest pipeline to enable semantic search, extract keywords and extract entities (using NER). The notebook can then be used to upload the sample data.

### Kibana

Once the data is ingested into your Elastic cluster it'll be ready to play with. Why not connect up an LLM and jump into Elastic Playground to start conversing with your data. Some sample questions to try:

- I'm interested in weekend warhero, what are they chatting about?
- Who else is discussing cars?

Importing the dashboard (using Kibana Saved Objects API) will provide visualisations to explore the keywords, entities and other data gleaned from the dataset during the ingest process.

Semantic Search is available out of the box (if you started an ELSER inference endpoint). Try some semantic queries like, 'text_semantic: movie discussions'.

## License

This project is licensed under the MIT terms, as detailed in the [LICENSE](LICENSE) file.
