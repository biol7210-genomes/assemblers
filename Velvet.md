Velvet is an algorithm which handles de novo genome assembly and short read sequencing (25 to 50 bp). 
This is done by manipulating the de Bruijn graphs to eliminate errors and resolve repeats. For very short paired-end reads, Velvet can produce contigs of significant length, up to 50-kb N50 length in simulations of prokaryotic data and 3-kb N50 on simulated mammalian BACs.

The algorithm has 4 stages:

1. Hashing the reads into kmers : For each kmer observed in the set of reads, the hash table identifies the ID of the first read 
encountered containing that kmer and the position of its occurrence within the read. Also the reverse complement of the kmer is recorded.
The value of k is limited by the length of the read being hashed, so that there is a small amount of overlap. For example, for read length 
of 25, k is set to a max of 21. Also to ensure that no kmer is its own reverse complement, value of k is odd.
Another database is created with opposite information. For a read, if its original kmers overlap with overlaps with subsequent reads, 
then they are cut. A node is created for the uninterrupted sequence of kmers for a read.

2. Construction of graph : Once the nodes are created, the graph is created by creating a directed arc from one node to the next by knowing
correspondence between the original kmers and the newly created nodes. Simplification of graph is done by merging two nodes when one of 
them has an outgoing arc to the other node and the other node has only an incoming arc.

3. Correcting Errors : Velvet focusses on three types of erroneous structures : tips , bubbles and erroneous corrections. 
A node is considered a tip and should be erased if it is disconnected on one of its ends, the length of the information stored in the node
is shorter than 2k, and the arc leading to this node has a low multiplicity (number of times the arc was found during the construction of
the graph) and as a result cannot be compared to other alternative paths. Once these errors are removed, the graph once again undergoes 
simplification.
Bubbles are generated when two paths start and end at the same nodes. Normally bubbles are caused by errors or biological variants. These
errors are removed using the Tour Bus algorithm, which is similar to a Dijkstra's algorithm, a breadth-first search that detects the best 
path to follow and determines which ones should be erased.
Erroneous corrections : These are connections that do not generate correct paths or do not create any recognizable structures within the
graph. Velvet erases these errors after completion of the Tour Bus algorithm, applying a simple coverage cut-off that must be defined 
by the user.

4. Resolving Repeats 
