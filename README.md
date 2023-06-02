# Exploring the Impact of Vector Search in E-Commerce

This repository contains a set of Jupyter notebooks that walk you through the necessary steps to compare multiple search systems (a BM25-based and vector-based ones) against each other.

This example compares an Elasticsearch based e-commerce search setting (["Chorus - the Elasticsearch edition"](https://github.com/querqy/chorus-elasticsearch-edition)) with and without using vectors.

The methodology is explained in the blog post ["How to Compare Vector Search to Traditional Search for E-Commerce"](https://opensourceconnections.com/blog/2023/04/20/how-to-compare-vector-search-to-traditional-search-for-e-commerce/).

## Prerequisites

* Jupyter
* Docker 
* `trec_eval` command line tool (see [https://aldolipani.com/trec_eval-installation-usage-and-behaviour/](https://aldolipani.com/trec_eval-installation-usage-and-behaviour/) for installation help)

## Notebooks

The notebooks in the folder `notebooks` contain all necessary code with additional explanation. They are enumerated in the order you should execute them to follow the methodolody.

### 0. Transform Ratings.ipynb
Queries are extracted from the provided ratings file and the ratings are transformed to the format `trec_eval` can work with. 
### 1. Query Elasticsearch.ipynb
Results from the Elasticsearch based settings are retrieved from Chorus, the Elasticsearch edition.
Five runs are executed: default, boost by vector image, match by vector image, boost by text vector and match by text vector.
### 2. Evaluate the Results.ipynb
The five result sets are compared via `trec_eval`. The metric used is nDCG.
### 3. Test Statistical Significance.ipynb
Check the `trec_eval` results for statistical significance.

## Setup

1. Clone this repository

`git clone https://github.com/wrigleyDan/data-science-regensburg-vector-search.git`

2. Clone the Chorus (Elasticsearch edition) repository

`git clone https://github.com/querqy/chorus-elasticsearch-edition.git`

3. Run the quickstart script to have Chorus up and running with vectors enabled

`cd chorus-elasticsearch-edition`

`./quickstart.sh -vector`

Alternatively, you can run the quickstart with the additional option `-lab` and go through the first Kata to get familiar with the Chorus stack. It guides you through the steps to optimize a query via search management:

`./quickstart.sh -vector -lab`

4. Run Jupyter in the repository directory

`cd ../data-science-regensburg-vector-search`

`jupyter notebook`

5. Access the first notebook and run through the cells

By default, Jupyter runs on port 8888, so go visit Jupyter and navigate to the first notebook (at http://localhost:8888/notebooks/notebooks/0.%20Transform%20Ratings.ipynb if you're running Jupyter on the default port) 
