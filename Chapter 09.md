## a. Can you describe a very simple evaluation setup, in which pairs of (query, document) are associated with relevant/non-relevant flags?

The query, document pair (q,D) is flagged as relevant if the document D is relevant for q.

## b. In the above setup, given a query, can you explain what precision is?

Precision is the ratio of the relevant documents returned to all returned document. (Mnemonic would be "High precision means no mistake")

## c. In the above setup, given a query, can you explain what recall is?

Recall is the ratio of the returned relevant documents to all relevant documents. (Mnemonic would be trying to recall all relevant document)

## d. In the above setup, given a query, can you explain what accuracy is?

Accuracy is the ratio of correctly classified documents to all documents.

## e. In the above setup, given a query, can you explain what specificity is?

Specifity is the ratio of all correctly not returned document to all non-relevant document.

## f. Can you easily compute each of the above quantities given concrete numbers?

Yes, I'll just apply the formula

## g. Can you explain why accuracy is a poor evaluation measure and how it can very easily be "hacked"?

**It is only possible when there is a large class imbalance between relevant and non-relevant documents!** This is usually the case however because most of the time you have a large collection of documents about a variety of topics (e.g. google). Given that there are more non-relvenat (we should absolutely say irrelevant though) documents, a classifier that always returns nothing will have an accuracy close to 1.

## h. Can you explain the precision vs. recall curve in the context of ranked retrieval?

You have two axis, one is the recall, the other one is the precision. You return documents.   
If the next returned document is relevant, then your precision increases (unless you are at 1) and your recall increases too.  
If the next returned document is non-relevant, then your precision decreases and your recall stays the same.

## i. Can you tell when such a curve tells us the system has high quality, or poor quality?

Ideally, we only select relevant documents and the precision stays always 1. A poor engine would have a precision of 0 (the inverted classification trick doesn't apply here because it is infeasible to just return all but 30 documents from the entire internet).

## j. Can you explain what the ROC curve does? Do you know what it plots against what? Do you understand the analogy with metal detectors?

ROC plots the Recall against the ratio of all incorrectly not returned documents to non-relevant documents (1 - specificity).
