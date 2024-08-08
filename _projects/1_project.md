---
layout: page
title: Paper Recs
description: 
img:
importance: 1
category: 
---

The Project aims to _automate_ _fetching_ _relevant_ _research papers_ to users on a timely basis.

### What Automation?
There are two scripts for this project    
    
    init-script.py
    script.py
    
The first script is used to initialize the recommendation system.

The second script is run recurrently from time to time to fetch for the papers.

### From where is the Fetching happening?
We use [Axriv API](https://info.arxiv.org/help/api/user-manual.html#arxiv-api-users-manual) to fetch for research papers.

### How are the papers Relevant?
We make use of your Zotero account to consider which papers are relevant to you.

We will consider a specific tag from your library and get relevant papers based on them.

### How does the Recommendation work?
We use a BERT model called [SciNCL](https://huggingface.co/malteos/scincl), pre-trained to differentiate between various types of scientific papers.

SciNCL outputs an embedding for each paper and we store them using [Pinecone](https://www.pinecone.io/) Vector Database.

After we have a stored a set of embedding in our collection, we can query the database with a new embedding to check for its relevance.

If the new paper passes a predefined threshold value, we recommend the paper to the users.


### Pre-requisite
Users are required to set certain environment variables.

Users are required to create an appropriate config.py file with the following variables.

{% raw %}

```html
ZOTERO_LIBRARY_ID : #Your Zotero userID for use in API calls

ZOTERO_API_KEY : #Your private Zotero API key

ZOTERO_TAG : #Desired tag from your Zotero library

PINECONE_API_KEY : #Your Pinecone API key

CHECKPOINT_PATH : #Path to the model checkpoints for the scincl model - Downloaded from Huggingface

INDEX_NAME : #Your desired index name for the Vector DB 

NAMESPACE_NAME : #Your desired namspace name for the collection in the Vector DB
```

{% endraw %}


#### Why Zotero
#### Why Arxiv
#### Why Pinecone
#### Why SciNCL
#### Why Automation

<iframe src="https://weedoo-research-paper-recommendation-system.hf.space" width="500" height="500" style="border:0;"></iframe>
