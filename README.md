# Evaluating Vector Search

This repository contains a set of Jupyter notebooks that walk you through the necessary steps to compare two search engines (a BM25-based one and a vector-based one) against each other.

This example compares an Elasticsearch based e-commerce search setting (["Chorus - the Elasticsearch edition"](https://github.com/querqy/chorus-elasticsearch-edition)) with a Jina AI based vector search setting.

The methodology is explained in the blog post ["How to Compare Vector Search to Traditional Search for E-Commerce"](https://opensourceconnections.com/blog/2023/04/20/how-to-compare-vector-search-to-traditional-search-for-e-commerce/).

## Prerequisites

* Jupyter
* Docker 
* JCloud account with Jina AI (you can register for free - as this repository is being created - at [https://jina.ai/](https://jina.ai/))
* `trec_eval` command line tool (see [https://aldolipani.com/trec_eval-installation-usage-and-behaviour/](https://aldolipani.com/trec_eval-installation-usage-and-behaviour/) for installation help)

## Notebooks

The notebooks in the folder `notebooks` contain all necessary code with additional explanation. They are enumerated in the order you should execute them to follow the methodolody.

### 1. JCloud Deployment.ipynb
This notebook deploys a flow to JCloud, downloads the product data, creates embeddings and indexes it. 
### 2. Transform Ratings.ipynb
Queries are extracted from the provided ratings file and the ratings are transformed to the format `trec_eval` can work with. 
### 3. Query JCloud.ipynb
Results from the Jina AI setting are retrieved from JCloud.
### 4. Query Elasticsearch.ipynb
Results from the Elasticsearch based setting are retrieved from Chorus, the Elasticsearch edition.
### 5. Evaluate the Results.ipynb
The two result sets are compared via `trec_eval`. The metric used is nDCG@10.
### 6. Test Statistical Significance.ipynb
Check the `trec_eval` results for statistical significance.

## Setup

1. Clone this repository

`git clone https://github.com/o19s/vector-search-evaluation.git`

2. Clone the Chorus (Elasticsearch edition) repository

`https://github.com/querqy/chorus-elasticsearch-edition.git`

3. Run the quickstart script to have Chorus up and running

`cd chorus-elasticsearch-edition`

`./quickstart.sh`

Alternatively, you can run the quickstart with the option `-lab` and go through the first Kata to get familiar with the Chorus stack. It guides you through the steps to optimize a query via search management:

`./quickstart.sh -lab`

4. Run Jupyter in the repository directory

`cd ../vector-search-evaluation`

`jupyter notebook`

5. Access the first notebook and run through the cells

By default, Jupyter runs on port 8888, so go visit Jupyter and navigate to the first notebook (at http://localhost:8888/notebooks/notebooks/1.%20JCloud%20Deployment.ipynb if you're running Jupyter on the default port) 

