##  a. Can you explain how a collection of documents can be abstracted away? Can you describe what the list-of-words, set-of-words and bag-of-words models preserve, and what they do not preserve?

There are multiple ways, in the lecture we saw the Incidence Matrix (M_i,j = 1 iff term i is in document j) and the inverted index. In a higher level view, we abstracted documents from list-of-words, to set-of-words and we linearizied that to a vector of booleans.
|                    | set of words | bag of words | list of words |
|--------------------|--------------|--------------|---------------|
| Allows duplicates? | no           | yes          | yes           |
| Is ordered?        | no           | no           | yes           |

they all also preserve inclusion but I omitted it from this table.


## b. Can you describe the query language of a Boolean retrieval system?

A boolean query can consists of words, and the operators `NOT`, `AND`, `OR` (and could use wildcards with `*` but it's not true here.)

## c. Do you know which model (list-of-words, set-of-words or bag-of-words) a Boolean retrieval system uses?

For a Boolean retrieval system, set-of-words suffices.

## d. Can you formulate this model by relating documents to words in a simple sentence?

Documents are sets. A word w is in the set of document D iff w is present in D (I would've suggested the standard inverted index but then the question e makes no sense).

## e. Can you build a standard inverted index from a collection of documents that has been abstracted away to the above model? (ignoring issues on lemmatization and stemming, etc).

Yes we can. Here is an algorithm we could apply
```
S <- standard inverted index (a dictionary of Words : List of DocID)
for D in Documents:
  for w in words of D:
    if w not in S:
      add w to S
    add D to S[w]
``` 

## f. Can you explain why the standard inverted index is logically equivalent to a term-document matrix populated with 1s and 0s?

Let the term-document matrix be called M, the standard inverted index S.
If the word w is in D then: $M_{w,D} = 1$ and $S[w] \in D$
If the word w is not in D then: $M_{w,D} = 0$ and $S[w] \notin D$

## g. Can you execute, in your head, a Boolean query like "ETH AND Zurich" given a standard inverted index?

See h. Do that in your head.

## h. Can you implement an index lookup for queries like "ETH AND Zurich"? (Hint: intersection or union of posting lists).

```
lookup(q):
  match q:
    q1 AND q2 -> return lookup(q1) INTERSECTION lookup(q2)
    q1 OR  q2 -> return lookup(q1) UNION lookup(q2)
    NOT q1    -> return D - lookup(q1)
    otherwise -> return S[q]
```
    
## i. Can you explain, on simple queries, how execution can be optimized by looking terms in the right order?

To save some time during the exam, always go for the term with a smaller cardinality in the standard inverted index. If the expression becomes more complicated, always evaluate that part of the query that has the least amount of elements.
