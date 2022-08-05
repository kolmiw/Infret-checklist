a. Can you explain how, from a document, we can generate a language model that can be used to generate similar documents?
b. Can you express such a model in terms of probability distribution on k-grams of words plus a stop probability? Do you see the link with Markov chains?
c. Can you express this model in terms of an automaton with probability on transitions?
d. Would you be able to implement a very simple software that "simulates" Sir Arthur Conan Doyle or Shakespeare with an adjustable degree of "faithfulness"?
e. Given a document, can you generate a k-gram model for any value of k?
f. Given a k-gram model and a document, can you compute the probability that the
model generates this document?
g. Can you explain how, by generating a model for each input document in a
collection (for some value of k), we can design an information retrieval scheme to execute a query? What criterion must the top returned document fulfill?
h. Can you tell whether language models in general are based on lists, sets or bags of words?
i. Can you explain why unigram models are special compared to higher values of k? How we can turn unigram models into bag of words using the multinomial distribution to compensate for permutations?
j. Can you explain what smoothing is and why it is needed?
k. Do you know what information retrieval system we "happen" to come back to,
using the above approach, under simplifying assumptions?