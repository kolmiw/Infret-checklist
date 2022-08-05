a. Can you explain which extra steps are needed, in practice, before indexing a collection of documents?
b. Can you explain what tokenization means? Lemmatization? Stemming?
c. Do you know what a stop word is?
d. Do you know how the UTF-8 encoding works, and how it relates to Unicode?
e. Do you know how the ASCII encoding works, and how it relates to Unicode?
f. Do you know the difference between a word and a type? (when types are used, we
consider "type" and "term" to be synonymous for the purpose of the lecture)
g. Do you know the difference between a document and a posting? Can you explain
why a posting is stored with just a document ID in an inverted index, even though it
is logically a (document, term) pair?
h. Can you describe how queries can be done by grouping words into equivalence
classes (called types), and how the standard inverted index can be built on types
instead of words?
i. Can you explain how, alternatively, expansion can be done, either on the query, or
on the index, and why it is more generic than equivalence classes?
j. Can you name a few stemmers?
k. Do you know what skip pointers are and how they can optimize querying? Do you
know the ideal length of such pointers?
l. Can you explain how the standard inverted index can be changed to a bi-word index
to handle phrase search?