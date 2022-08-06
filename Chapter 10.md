## a. Do you know all the basics of probabilities (Omega space, definition of a probability, event, disjoint events, independent events, conditional probabilities, random variables, addition rule, etc., etc.)?

Yes, I passed wus

## b. Do you know how to and how NOT to write probability formulas involving random variables (i.e., P(X) and P(x) are bad notations)?

The stuff in parentheses is literally what you're looking for. Btw it's $P(X=x)$ or $p_X(x)$

## c. Do you know Bayes rules and, independently of its interpretation, can you prove it easily using basic probability rules?

Yes Bayes rule says that $P(A | B) = \frac{P(B|A)*P(A)}{P(B)}$. But I think remembering it as $P(A|B) * P(B) = P(B|A)*P(A)$ is easier

The proof is the following:  
$P(A \cap B) = P( B | A ) * P(A)$.  
but since the intersection is a commutative operation it must also hold that:  
$P(A \cap B) = P( A | B ) * P(B)$.  
Hence you can match the two RHS's into one eqution.   
$P( A | B ) * P(B) = P( B | A ) * P(A)$.   
now divide both sides by $P(B)$.   
$P(A | B) = \frac{P(B|A)*P(A)}{P(B)}$.



## d. Are you able to use Bayes rule in a very basic setting (given three numbers, compute the fourth one)? Can you tell which factor is the prior? Which factor is the posterior?

For an event A, prior is $P(A)$ and the posterior is $P(A|B)$ for the other event B.

## e. Can you explain how we can "imagine" an Omega space with documents as random variables, queries as random variables, relevance as random variables, and it makes sense to write formulas such as P(D=d), P(R|D=d and Q=q), etc., to model the probability that a document is relevant to a query?

We can say that the Omega space is $D \times Q \times R$, and we interpert $P(R|D=d \text{ and } Q=q)$ as the probability that the document d  is deemed relevant for query q.

## f. Can you explain in very simple terms how a very simple Boolean retrieval system can be built (that is, giving a query q, saying whether a document d is returned or not) using such a framework, assuming the probabilities are all known?

For a query q, we return document d iff $P(R|D=d \text{ and } Q=q) > r$ for some $ r \in [0,1] $ (but we've seen 0.5 as an example).

## g. Can you explain, on a high-level, how Bayes' formula can be applied to compute P(R|D=d and Q=q) and use this as a scoring system? 
##### Note: you do not need to know all the details that follow on how this formula is further derived. If you know how Bayes' rules can give us P(R|D=d and Q=q) = P(D=d|R and Q=q) * P(R|Q=q) / P(D=d|Q=q), then you will be fine.

1. on a very high level, I want to use the connection between R and d here, i.e. $P(R|D=d \text{ and } Q=q) * P(D=d \text{ and } Q=q)  = P(D=d|R text{ and } Q=q) * P(R \text{ and } Q=q) $

## h. Can you explain why the assumption that terms appear independently from each other in documents makes sense? Do you see that this means that the probabilities on the terms can simply be multiplied to find the probability of the document?

The only reason we do this is that we don't lose that much precision while we make our life much easier by this.

## i. Can you tell whether the probabilistic models we covered are based on sets, bags or lists of words?

Set of words

## j. Do you know what information retrieval system we "happen" to come back to, using the above approach, under simplifying assumptions?

ranked retrieval with tf-idf

## k. Can you explain what maximum likelihood estimation is?

We estimate parameters by computing what is the most likely value for this parameter, given our realised results.
