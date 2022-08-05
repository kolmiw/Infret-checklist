## a. Can you explain which extra steps are needed, in practice, before indexing a collection of documents?

We need to collect documents (don't hate the messenger, this is actually on the slides kek), tokenize it and usually preprocess with stemming or lemmatization.

## b. Can you explain what tokenization means? Lemmatization? Stemming?

Tokenization:
  - Basically parsing unless I'm mistaken. We take a string of characters as input and create words/tokens out of it

Lemmatization:
  - The procedure of chopping of the end of the word, with the use of a vocabulary and morphological analysis of words, normally aiming to remove inflectional endings only and to return the base or dictionary form of a word, which is known as the lemma

Stemming:
  - Lemmatization but using much simpler heuristic by applying stemmer rules

## c. Do you know what a stop word is?

Words appear in (almost) every document (hence have a high collection frequency) so it is not worth it to add them as a posting to the standard inverted index.

## d. Do you know how the UTF-8 encoding works, and how it relates to Unicode?

I'm pretty sure we didn't cover Unicode itself, only through UTF-8. UTF-8 can encode characters with at most 4-bytes, where (I didn't find a good mnemonic to remember it, feel free to suggest one)

| Code point up to | Byte 1   | Byte 2   | Byte 3   | Byte 4 |
|------------------|----------|----------|----------|--------|
| U+007F           | 0XXXXXXX |          |          |         |
| U+07FF           | 110XXXXX | 10XXXXXX |          |         |
| U+FFFF           | 1110XXXX | 10XXXXXX | 10XXXXXX |         |
| U+10FFFF(?)      | 1110XXXX | 10XXXXXX | 10XXXXXX |10XXXXXX | 


## e. Do you know how the ASCII encoding works, and how it relates to Unicode?

Ascii consists of 1 byte per char. The first 128 characters in the unicode catalogue is defined to match the Ascii table

## f. Do you know the difference between a word and a type? (when types are used, we consider "type" and "term" to be synonymous for the purpose of the lecture)

Words are sequences of characters, types are equivalnce classes between words (see [h](#h-can-you-describe-how-queries-can-be-done-by-grouping-words-into-equivalence-classes-called-types-and-how-the-standard-inverted-index-can-be-built-on-types-instead-of-words) lmao). E.g. "Zürich" and "ZH" are two different words but would be the same type.

## g. Do you know the difference between a document and a posting? Can you explain why a posting is stored with just a document ID in an inverted index, even though it is logically a (document, term) pair?

A Document is just a (finite) stream of words, while a posting is an indicator that a term exists in a document. The posting can be only stored as a document ID in the standard inverted index, because each posting belongs to a term.

## h. Can you describe how queries can be done by grouping words into equivalence classes (called types), and how the standard inverted index can be built on types instead of words?

We can first check if a query word belongs to an equivalence class. If yes, then we convert the term to the common identifier of that class. The standard inverted index can be built in the same way as with words, but before instead of checking if $w \in S$ we can check if $type(w) \in S$.

## i. Can you explain how, alternatively, expansion can be done, either on the query, or on the index, and why it is more generic than equivalence classes?

What is an expansion?

## j. Can you name a few stemmers?

Porter, Lovins and Paice

## k. Do you know what skip pointers are and how they can optimize querying? Do you know the ideal length of such pointers?

Skip pointers are additional pointers in a (sorted) list. It is used to accelerate the search of a term. During a query, if the skip pointers value is still smaller than the value we are looking for, we can skip the line ("succesfully follow the skip pointer") and continue or search there. The ideal length was proposed to be $\sqrt{|n|}$ where n is the length of the list.

## l. Can you explain how the standard inverted index can be changed to a bi-word index to handle phrase search?

It should not be possible with a standard inverted index (S) as it uses a set-of-documents and it is not denoting the order of the words (then it wouldn't be standard anymore). If we can access the documents though, then we can just create a new standard inverted index of bi-words.

## m. Can you explain how the standard inverted index can be changed, alternatively, to a positional index (that is, with positional postings) to handle phrase search? Which model (list/set/bag of words) is then supported?

For each term, instead of a simple list of Document IDs, we can store a list tuples of Document ID's and a set of positions. This wording is too tragic, let me write this out with an example:

```
D1: "ETH Zürich is not a company, but is located in Zürich"
D2: "My ETH investment is insured by the Zürich Insurance company"
```
then
```
S["Zürich"] = [(D1, [2, 11]), (D2, [8])
```
## n. Can you explain why the first of the above solutions may have false positives, while the second one doesn't?

Oh so you wanted me to just accept a document having a bi-word if both words are in the document didn't you? In that case, the phrase "ETH Zürich" would be a false negative in the first approach, but not the second one.
