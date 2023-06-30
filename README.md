##Chromadb Collection and Query Example
This code snippet demonstrates how to use the chromadb library to create a collection, add documents with metadata to the collection, and perform a query on the collection.

#Installation
Before running the code, make sure you have the chromadb library installed. You can install it using pip:

```
pip install chromadb
```
Usage
Import the necessary modules and classes:

from chromadb import Client
from chromadb.config import Settings
#Create a Client object:
```
client = Client(Settings(
    chroma_db_impl="duckdb+parquet",
    persist_directory="/path/to/chroma-db" # Optional, defaults to .chromadb/ in the current directory
))
```
#Define the documents and metadata:

```
string_1 = "Video games are an interesting class of software..."
string_2 = "The #1 reason I started to consider buying an iPad..."

metadata_1 = {'source:1': 'video_games'}
metadata_2 = {'source2': 'ipad_issues'}
```

#Create a collection and add the documents with metadata:

```
collection = client.create_collection("docs")
collection.add(
    documents=[string_1, string_2],
    metadatas=[metadata_1, metadata_2],
    ids=["id1", "id2"]
)
```
#Perform a query on the collection:

```
results = collection.query(
    query_texts='why do you think video games are interesting?',
    n_results=1
)
```

#Print the result:

```
print(results['documents'][0])
```
## Additional Notes
- The chromadb library provides a convenient way to store and query collections of text documents with associated metadata.
- The Settings object allows you to configure the underlying database implementation and the persistence directory.
- The add() method is used to add documents to the collection. Each document is associated with an ID and can have metadata associated with it.
- The query() method allows you to search the collection for documents that match a specific query text. The n_results parameter determines the number of top matching documents to retrieve.
- The result of the query is a dictionary containing the matching documents and their metadata.
- Feel free to modify the code and customize it according to your needs. Happy coding!
