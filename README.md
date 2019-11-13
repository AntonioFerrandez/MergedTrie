# MergedTrie
MergedTrie code

Example of the usage of the MergedTrie. Please quote it as:
Ferrandez A, Peral J (2019) MergedTrie: Efficient textual indexing. PLoS ONE 14(4): e0215288. https://doi.org/10.1371/journal.pone.0215288

This is the C++ code to run the term-level index of string-words (with additional data associated to each word) called MergedTrie. 
It supports keyword insertion, search, modification, deletion, listing and prefix listing.

Usage:
  * Uncompress MergedTrie.tgz
  * #include "MergedTrie.h" in the files that will use it with no data: "MergedTrie trie2;" or with data: "D_MergedTrie<char> trie1;"
  * The file "mainMergedTrie.cpp" shows the main functionalities of the data type

Please, report any comment about it to antonio@dlsi.ua.es

The main theoretical contributions of our proposal in comparison with previous types of Tries:
1.	The MergedTrie extends the Double Trie (DT) structure (Morimoto et al. 1995; Aoe et al. 1996) in the following ways:
  •	It enhances the DT segmentation of the term in order to achieve a reduction in the height of the Trie by segmenting the term at exactly half its length.
  •	It merges the two Tries in DT into a single one, in order to achieve both prefix and suffix overlapping in the terms to be indexed. Thus, it achieves a great decrease in the number of nodes and memory consumption.
2.	It results in a great reduction in memory consumption, both in states/nodes and edges and in the prefixes and suffixes of the indexed terms, overcoming the problem of the significant cost of update operations as occurs when compacted or minimized segments need to be split or merged in the DAWG, ADFA and CDAWG structures.
3.	It does not require prior term sorting, compression or decompression processes, as occurs in other “compact” structures or representations.
4.	It keeps the complexity of the insertion, search, modification and deletion operations proportional to the length of the string, in contrast to DAWG/ADFA structures, where this is proportional to the number of nodes/states.
5.	The efficiency is also improved because the MergedTrie updating operations are based on simple Trie operations.
6.	It facilitates the indexation of additional information (e.g. n-grams, phrases, bitexts, biwords or additional data) related to the words stored in all the MergedTries, because it automatically provides word identifiers that different MergedTries can share.

Regarding the practical impact of our research:
1.	It has been implemented in C++ and has been comparatively analyzed with the Hash Table, Trie, Crit-bit, ADFA-DAWG, double-array, Double Trie and Minimal-Prefix Trie (with and without string labels), showing an important reduction in memory consumption and number of nodes/edges.
2.	Its sequential implementation allows for quite simple and efficient de/serialization of the MergedTrie from/into the disk. It achieves an efficient storage in secondary memory, optimizing the subsequent load times and allowing direct access to the structure when it is stored in secondary memory if it does not fit in the main memory due to the number of keys to be indexed.
3.	It requires less space than the original text to be indexed.
4.	Regarding temporal efficiency, it especially improves insertion operations, as well as allowing new insertions and updates, in contrast to the static structures that  only allow for the search operation.
5.	An additional compaction operation is provided in order to improve the computational efficiency of the structure.
  
Abstract:
The accessing and processing of textual information (i.e. the storing and querying of a set of strings) is especially important for many current applications (e.g. information retrieval and social networks), especially when working in the fields of Big Data or IoT, which require the handling of very large string dictionaries. Typical data structures for textual indexing are Hash Tables and some variants of Tries such as the Double Trie (DT). In this paper, we propose an extension of the DT that we have called MergedTrie. It improves the DT compression by merging both Tries into a single and by segmenting the indexed term into two fixed length parts in order to balance the new Trie. Thus, a higher overlapping of both prefixes and suffixes is obtained. Moreover, we propose a new implementation of Tries that achieves better compression rates than the Double-Array representation usually chosen for implementing Tries. Our proposal also overcomes the limitation of static implementations that does not allow insertions and updates in their compact representations. Finally, our MergedTrie implementation experimentally improves the efficiency of the Hash Tables, the DTs, the Double-Array, the Crit-bit, the Directed Acyclic Word Graphs (DAWG), and the Acyclic Deterministic Finite Automata (ADFA) data structures, requiring less space than the original text to be indexed.
