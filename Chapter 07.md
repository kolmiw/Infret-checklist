## a. Can you explain how, say, a Boolean retrieval system can be extended with search on fields like title, abstract, authors (parametric search)?

Instead of having one field in the document, now you have multiple fields with different weights.

## b. Can you explain how this can lead to a "primitive and simple" scoring system?

## c. Which is the model (set/list/bag of words) underlying the vector space model?

Bag of words as now we care about the term frequency, but we still don't care about order.

## d. Can you explain what a term frequency is, given a term and a document?

given term t and document D, the term frequency describes how often the term t occurs in document D

## e. Can you explain what a document frequency is, given a term?

given term t, the document frequency describes how many documents containt the term t

## f. Can you explain what a collection frequency is, given a term?

given term t, the collection frequency describes how often the t occurs in the entire collection

## g. Can you explain how inverse document frequency (idf) is defined and why it is a better tool than "raw" document frequency?

We are looking for an index that is higher if a term is less frequent, as those are more likely to be important to the query.
the idf is defined as $idf(D,t) = log( \frac{|\text{Documents}|}{df_{t}}) $

## h. Can you easily compute the tf-idf of a term/document pair, given a collection expressed in the bag of words model?

Hopefully we get values that is easy to compute (or we even get the idf). What you then do is just multiply the $tf_{t,D}$ with $idf(D,t)$ (sorry for the notation)

## i. Can you explain how, in the bag of words model, documents are vectors of numbers?

Let T denote the number of tokens. Then a document can be represented a vector: $(f(t_1), f(t_2),  ... , f(t_T)) $ where f could be the term frequency, the td-idf or other weighting schemes.

## j. Can you explain why the Euclidian norm makes sense for documents?

The Euclidian norm describes the length of a vector. To avoid a bias towards vectors that happen to be longer, we can use the Euclidian norm to renormalise the vectors.

## k. Can you renormalize a document expressed as a vector?

$\frac{1}{||v||} * v$

## l. Can you explain why the inner product between two (renormalized) documents gives a good hint on their similarity (cosine similarity)?

The inner product of a,b describes the length of the vector a if it was projected onto b (this is a commutative/symmetric) operation. The longer the projection, the smaller is the angle between the vectors (and larger the scalar product) the more similar are the two documents.

## m. Can you compute the inner product of two documents expressed as vectors?

$\sum_{i=0} x_i * y_i$

## n. Can you explain why a query can also be seen as a vector of numbers?

The query can be seen as a document itself.

## o. Can you explain why the inner product between a (renormalized) document and query is a good scoring system?

Because the higher the inner product, the higher the similarity between the query and a document (see l)

## p. Can you explain how the standard inverted index can be extended and adapted to support cosine similarity computation?

Instead of Doc-id we can store the tf-idf (but it would take a lot of space) or just the term frequency and store the idf instead of document frequency (more space efficient)

## q. Can you explain the difference between term-at-a-time and document-at-a-time score computation, given a query?

Term-at-a-time iterates through the terms and computes the tf-idf of a term for every documents of it's postings. Document-at-a-time iterates through documents and computes the tf-idf of a document for every term it has.

## r. Can you manually compute scores, given an inverted index adapted to ranked retrieval (i.e., storing precomputed idfs as well as term frequencies for each posting)?

It depends on the tf-idf variants. There is no way I'll recall a log ave term frequency. Otherwise you just check the variant of the smart notation. The first 3 letters denote the document weights, the second 3 denote the query weights.

## s. Are you familiar with the SMART notation, in particular, do you know what it expresses (you must know at least the letters n, a and b for the term frequency, n and t for the document frequency, and n and c for normalization)?

The three letters denote the: term frequency, document frequency and normalisation:

| term frequency             | document frequency | normalisation   |
|----------------------------|--------------------|-----------------|
| n = tf_t,d                | n = df_t           | n = 1           |
| t = tf-idf                 | t = idf            | c = 1/\|\|v\|\| |
| a = a + (1-a) tf_td/maxt |                    |                 |

where maxt t = max_t (tf_t,d)
