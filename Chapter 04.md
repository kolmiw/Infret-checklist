## a. Can you give the two search structures (hash index, B+-Tree) mainly used in practice for lookup up a term and its posting list in the standard inverted index?

What?

## b. Can you explain, on a logical level, what a B+-tree looks like, and explain the constraints on it?

It is a binary tree but with multiple children. A B+-tree usually has an upper-and a lower bound of children. Unlike B-Trees, B+-Trees don't have values on non-leaf nodes, the parent nodes only have pointer to their children.

## c. Can you insert, delete and lookup a term into or from a B+-tree?


## d. Do you know the difference between a B-tree and a B+-tree?

See 3rd sentence of [b](#b-can-you-explain-on-a-logical-level-what-a-b-tree-looks-like-and-explain-the-constraints-on-it)

## e. Can you explain why spelling mistakes are a problem in the context of information retrieval?

Because if the spelling mistake would make the word into another word that exist in the posting (e.g. you want to write "bigger" but you have a typo and write "jigger" instead), it is difficult to tell that the user wants something else

## f. Can you explain how wildcard queries can be executed? Can you explain why trailing wildcards are easier?

A wildcard query can have the wildcard either:
- in the beginning: You can invert the posting list and the query as well and pretend it is a trailing wildcard
- in the end: You can just find the range of the B+-tree that still matches the prefix
- in the middle: (Let's say the search word is "Stati\*tics". You can cut the query in two pieces and search for both terms (here "Stati\*" and "\*tics" and then take their intersection). A post-filtering is needed to avoid false positives.

## g. Do you know what a permuterm index looks like?

you put dollar sign at the end of the word and then you introduce every single rotation. For example the permuterm index of the word "water" looks like this:
```water$, ater$w, ter$wa, er$wat, r$wate, $water```

## h. Do you know what the k-grams (k>=2) of a word are?

The k-grams of a word is the set of all k-long char-sequences that could be exactly matched to the words. For example, the 3-gram of the word "water" would be ```$wa, wat, ate, ter, er$```. We add the dollar signs which denote the beginning/end of the word.

## i. Can you explain what a k-gram index is and how it is similar in structure to a bi-word index?

The k-gram index is an index that maps k-grams to words that contain the given k-gram. It is similar to bi-word indices in sense that a bi-gram index is the same as the bi-word index but with characters instead of words (Not sure if this is what they want)

## j. Can you compute the Jaccard coefficient between two sets (expressing how close they are, i.e., a kind of "inverse distance")?

$J(A,B) = \frac{|A \cap B|}{|A \cup B|}$ an epic speedrun trick is to compute the intersection and then just go $=\frac{|A \cap B|}{|A|+|B|-|A \cap B|}$

## k. Can you apply the Jaccard coefficient to the sets of k-grams (for k >=2) generated from two words to estimate their proximity?

You compute the k-grams of the two words (see [h](#h-do-you-know-what-the-k-grams-k2-of-a-word-are) $W_1 = \text{kgram(w1)},  W_2 = \text{kgram(w2)}$. Then compute $J(W_1, W_2)$

## l. Can you explain what the edit (Levenshtein) distance between two words is?

It tells how many steps it takes to get from one word to another, where one step can either be (Adding, Removing or Replacing a single letter).

## m. Can you compute the edit distance between any two words using dynamic programming?

Well yes \(D[i][j] := editing distance of the substrings from 0-i and 0-j) but in the exam just look at the largest common substring (with a tolerance of 1) and just edit it from there. Should work unless the strings are insanely long.

## n. Can you explain what the Soundex algorithm does (without knowing its details by heart)?

something-something convert letter to numbers and values

## o. Do you understand how the above techniques are useful to address spelling errors?


