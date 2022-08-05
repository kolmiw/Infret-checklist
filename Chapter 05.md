## a. Do you know which storage media are involved in a system (disk, memory, CPU cache)? Do you know how they do in terms of relative storage capacity, speed?

All of them are involved, in terms of speed: CPU cache > memory > disk. In terms of capacity: CPU cache < memory < disk.

## b. Do you know the difference between latency and throughput?

Latency: What is the delay between someone starting to send data and the other party receiving it.
Throuhput: How much data can I put through within a given time-unit.

## c. Can you explain why data is transmitted in blocks to and from disk?

Because in the worst case, we have to wait until the disk rotates around an entire circle to get to the location where the data is stored. So fetching the data in blocks decreases the amount of unnecessary disk rotations.

## d. Do you know why caching is useful?

This is literally the only thing I remember from Design of Digital Circuits. From the cache it is faster to load blocks of the collection than from the disk.

## e. Can you explain how term IDs help compressing the size of a posting (we mean here a posting "on its own" as a document-term pair, that is, not the way it is stored within an inverted index)?

Since documents appear multiple times (since we sort by terms), it makes perfect sense to not use the entire document to denote it's existence but only some ID's that we can look up if needed.

## f. Can you explain how Blocked Sort-Based Indexing (BSBI) works, and the details of its two main steps?

Step 1: Create intermediate results, by loading blocks of the collection and sorting that block based on term-ids. That's in O(TlogT)
Step 2: Merge the results together.

## g. Can you explain how Single-Pass In-Memory Indexing (SPIMI) works, and the details of its two main steps?

Step 1: Similar to BSBI but we do not use term-ids for the intermediate result 
Step 2: Sort the terms

## h. Can you contrast BSBI from SPIMI in terms of differences and also complexity?

BSBI creates the term-ids first and then starts with indexing, while SPIMI just uses the terms and if the term is already in the dictionary then

## i. Do you know how MapReduce works?

The idea is to exploit distributed systems to accelerate the procedure of indexing. With map reduce you have two classes of contributors. You have mappers (or parser) who just take chunks of the data and create term-id,doc-id pairs (we called them key-value pairs for some reason). Then in a second run the reducers (or inverters) take the pairs from the mappers with a given term-id (it could be multiple term-ids) and create the inverted index for the terms they were assigned to.

## j. Can you explain how MapReduce is also a good way of constructing an index? Can you easily explain what the map and reduce functions are and what they manipulate?

Mappers can just create a normal index from the block they received from the master node. Reducers compute the union of the postings they receive.

## k. Can you explain the challenges of online construction (i.e., new documents arrive on the fly, rather than being all known at the beginning)?

We have to update the posting lists regularly, as documents can get added, deleted and changed.

## l. Can you explain the auxiliary index approach to online index construction?

## m. Can you explain how logarithmic merging works and how it differs from an auxiliary index in terms of the compromise made between construction time and query time?

We can take two blocks with length n and merge them together. Doing this twice will leave us with 2 different n blocks that we can merge together. Doing this twice will leave us with 2 different 2n blocks that we can merge together, and so on. The construction time is in $\mathcal{O}(T log(\frac T n))$
