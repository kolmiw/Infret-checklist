a. Do you know which storage media are involved in a system (disk, memory, CPU cache)? Do you know how they do in terms of relative storage capacity, speed?
b. Do you know the difference between latency and throughput?
c. Can you explain why data is transmitted in blocks to and from disk?
d. Do you know why caching is useful?
e. Can you explain how term IDs help compressing the size of a posting (we mean here
a posting "on its own" as a document-term pair, that is, not the way it is stored
within an inverted index)?
f. Can you explain how Blocked Sort-Based Indexing (BSBI) works, and the details of its
two main steps?
g. Can you explain how Single-Pass In-Memory Indexing (SPIMI) works, and the details of its two main steps?
h. Can you contrast BSBI from SPIMI in terms of differences and also complexity?
i. Do you know how MapReduce works?
j. Can you explain how MapReduce is also a good way of constructing an index? Can
you easily explain what the map and reduce functions are and what they
manipulate?
k. Can you explain the challenges of online construction (i.e., new documents arrive on
the fly, rather than being all known at the beginning)?
l. Can you explain the auxiliary index approach to online index construction?
m. Can you explain how logarithmic merging works and how it differs from an auxiliary
index in terms of the compromise made between construction time and query time?