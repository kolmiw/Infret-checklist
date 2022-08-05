a. Can you explain how a collection of documents can be abstracted away? Can you describe what the list-of-words, set-of-words and bag-of-words models preserve, and what they do not preserve?

>
b. Can you describe the query language of a Boolean retrieval system?
c. Do you know which model (list-of-words, set-of-words or bag-of-words) a Boolean
retrieval system uses?
d. Can you formulate this model by relating documents to words in a simple sentence?
e. Can you build a standard inverted index from a collection of documents that has
been abstracted away to the above model? (ignoring issues on lemmatization and
stemming, etc).
f. Can you explain why the standard inverted index is logically equivalent to a term-
document matrix populated with 1s and 0s?
g. Can you execute, in your head, a Boolean query like "ETH AND Zurich" given a
standard inverted index?
h. Can you implement an index lookup for queries like "ETH AND Zurich"? (Hint:
intersection or union of posting lists).
i. Can you explain, on simple queries, how execution can be optimized by looking
terms in the right order?