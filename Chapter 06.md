## a. Do you know what Heap's law is and what it says (including its formula)?

Heap's law says that for T terms, there are about $k\*T^{n}$ tokens, where n is usually around 0.5 and k is around $30 \leq k \leq 100$. (My mnemonic is that there must be less tokens than terms)

## b. Do you know what Zipf's law is and what it says (including its formula)?

Zipf's law says that the k-th most common term is about $\frac 1 k$-times as frequent than the most common term (The mnemonic here is that Zip**F** is written as a **F**raction.

## c. Can you explain a few ways that the search structure to lookup terms can be compressed (e.g., blocked storage, front coding)?

Instead of storing the terms themselves, we can just store one long string of all postings and then use pointers + offsets to the terms instead of having th terms themselves in the posting. This is the blocked storage approach.

Front coding extends this with the idea, that instead of writing down every word in the string it suffices to just include the shared prefixes once, and then just write down the different paddings (e.g. instead of `automata automate automatic` you can write `automat*a,e,ic`.

## d. Can you explain why fixed-length encoding for posting lists (lists of document IDs) is not optimal in practice?

For most of the terms you'll have a surplus of bits (or even bytes) that you don't need. It could technically happen that you run out of space for Document-id but usually that doesn't happen.

## e. Can you explain how this can be improved with a variable-length coding (say, with 4- bit packets or 8-bit packets)?

Now instead of wasting multiple bits, we can a variable-length coding of integers, where you only use as many 4 (or however many)-bit packets as you need. You of course have to pay attention to add a continuation bit that indicates wether a packet is the last one or not. In the lecture, a continuation bit of 0 meant that this is not the final packet, and 1 meant that this is the final packet. (therefore, the 4-bit variable encoding for 5 was 1 101 and for 9 it was 0 001 1 001)

## f. Do you know what the unary (also called temperature) encoding is? Can you easily encode and decode an integer with a pen and paper?

It is just as many ones as the number you want to encode. I recommend grouping them as at most 5 1s next to eachother and then taking a small gap to have it easier.

## g. Do you know what the Elias Gamma Code is? Can you easily encode and decode an integer with a pen and paper?

The gamma code is a unary encoding of the length  of the integer in binary after the leading 1 is removed and then the binary itself is concatenated. My way to remember how to construct gamma code is the following: 
```
1. write down your integer in binary (e.g.: 11 -> 1011)
2. count it's length and subtract one (e.g. len(1011) = 4 so I take 3)
3. Write this many zeroes in fron of your number (1011 -> 000 1011)
4. Flip the leading zeroes and the first one from your intermediate result (000 1011 -> 111 0011)
```

## h. Do you know what a prefix code is? Do you know that the above three encodings are prefix codes?


## i. Do you know what a universal code is?

if the encoding of an entropy is provably within a reasonable factor of the optimal encoding for any arbitrary distribution of integers, we call it universal

## j. Do you know how the Elias Gamma Code does in terms of space, asymptotically? (without knowing the deepest details on information theory or Entropy)

We can prove (we as in humanity, not us during the exam) that for any distribution, the gamma encoding has an Entropy below 3 times the optimal encoding
