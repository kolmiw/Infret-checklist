a. Do you know all the basics of probabilities (Omega space, definition of a probability, event, disjoint events, independent events, conditional probabilities, random variables, addition rule, etc., etc.)?
b. Do you know how to and how NOT to write probability formulas involving random variables (i.e., P(X) and P(x) are bad notations)?
c. Do you know Bayes rules and, independently of its interpretation, can you prove it easily using basic probability rules?
d. Are you able to use Bayes rule in a very basic setting (given three numbers, compute the fourth one)? Can you tell which factor is the prior? Which factor is the posterior?
e. Can you explain how we can "imagine" an Omega space with documents as random variables, queries as random variables, relevance as random variables, and it makes sense to write formulas such as P(D=d), P(R|D=d and Q=q), etc., to model the probability that a document is relevant to a query?
f. Can you explain in very simple terms how a very simple Boolean retrieval system can be built (that is, giving a query q, saying whether a document d is returned or not) using such a framework, assuming the probabilities are all known?
g. Can you explain, on a high-level, how Bayes' formula can be applied to compute P(R|D=d and Q=q) and use this as a scoring system?
Note: you do not need to know all the details that follow on how this formula is further derived. If you know how Bayes' rules can give us P(R|D=d and Q=q) = P(D=d|R and Q=q) * P(R|Q=q) / P(D=d|Q=q), then you will be fine.
h. Can you explain why the assumption that terms appear independently from each other in documents makes sense? Do you see that this means that the probabilities on the terms can simply be multiplied to find the probability of the document?
i. Can you tell whether the probabilistic models we covered are based on sets, bags or lists of words?
j. Do you know what information retrieval system we "happen" to come back to, using the above approach, under simplifying assumptions?
k. Can you explain what maximum likelihood estimation is?