## a. Can you explain how we can optimize and make scoring computations faster, on the adapted inverted index seen in the previous section?

We can take a \*n\* variant of the tf-idf and then all we have to do is multiply the pre-computed tf with the pre-computed idf together.

## b. Do you know what inexact top-K retrieval is and why it makes sense?

Instead of searching for all documents, we are going to search only within a set of pre-selected document. You might think this would return inexact results, and while that is true, the document ranking would be an approximation already so we don't lose out on that much

## c. Can you explain a few strategies that enable an efficient implementation of inexact top-K retrieval (champion lists, impact ordering, clustering, tiered indices...)?

Champion list takes the idea that we pre-select the best r documents with the highest term frequency for every term in the query.  
Impact ordering just starts preselecting based on the document with the highest idf. It wasn't really said how we would exactly preselect the documents with impact ordering though
Clustering creates clusters of document. It works by randomly picking cluster leaders and then you only select the documents that are inside the cluster of the closest leader to the query.  
Tiered indices creates multiple classes of results. First you pick your Tier 1 result, then your Tier 2...etc


## d. Can you sketch a complete information retrieval architecture and its components?

Depending on the queries we allow, we might prefer:
| Query type         | Query interface    |
|--------------------|--------------------|
| Boolean query      | Inverted index     |
| Phrase query       | Biword index       |
| Wildcard query     | k-gram index       |
| Mistake tolerant query     | k-gram index       |
| Set of words       | Vector-space model |
| Field/Zone queries | Zone indices       |

The entire architecture then consits of:
  1. Parsing documents (you can apply stemming or lemmatization, eliminate stop words etc.)
  2. Build indices (see the interfaces above)
  3. Evalulate queries (parse it, check for spelling mistakes... etc)
  4. Evidence accumulation (compute documents scores)
  5. Return the results (optionally also rank them)
