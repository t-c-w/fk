# fk
Based on code from Julien Palard.

To install:	```pip install fk```

## Overview
The `fk` package provides a Python interface for managing and interacting with an Elasticsearch cluster. It includes functionality to perform CRUD operations on indices, handle bulk data insertion, manage mappings, and facilitate the reindexing of data with new mappings. The package is particularly useful for operations involving index migration or restructuring in an Elasticsearch environment.

## Features
- **ElasticSearch Class**: A class that provides methods to interact with an Elasticsearch instance. It supports operations such as `GET`, `POST`, `DELETE` requests, and specialized methods like `bulk_insert` for bulk operations and `scan_and_scroll` for efficient data retrieval.
- **Reindexing Utility**: A command-line utility provided to remap and reindex an Elasticsearch index. This is useful when the mappings of an index need to be changed and the data needs to be reindexed according to the new mappings.

## Installation
To install the `fk` package, run the following command:
```bash
pip install fk
```

## Usage

### ElasticSearch Class
Here is an example of how to use the `ElasticSearch` class to interact with an Elasticsearch instance:

```python
from fk import ElasticSearch

# Initialize the ElasticSearch object with the URL of your Elasticsearch instance
es = ElasticSearch('localhost:9200')

# Get data from an index
data = es.get('my_index/_doc/1')

# Post data to an index
response = es.post('my_index/_doc', {'name': 'John Doe', 'age': 30})

# Delete an index
response = es.drop('my_index')
```

### Command-Line Utility for Reindexing
The package also includes a command-line utility that can be used to change the mapping of an index and reindex the data. Here is how to use it:

```bash
python -m fk --elasticsearch localhost:9200 --index my_index --mapping path_to_mapping_file.json
```

### Function Documentation

- **scan_and_scroll(index)**: Iterates over all documents in the specified index using the Elasticsearch scan and scroll API.
- **set_mapping(index, mappings)**: Sets the mapping for the specified index. Mappings should be a JSON object defining the structure of the index.
- **count(index)**: Returns the count of documents in the specified index.
- **bulk_insert(index, bulk)**: Performs a bulk insert operation. The `bulk` parameter should be a list of documents to be inserted.
- **drop(index)**: Deletes the specified index.
- **alias(index, to)**: Creates or updates an alias for the specified index.

## Contributing
Contributions to the `fk` package are welcome. Please ensure that any pull requests or issues are relevant to the functionalities provided by this package and that they follow the existing coding style and structure.