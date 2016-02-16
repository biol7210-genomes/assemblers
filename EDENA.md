#EDENA(Exact DE Novo Assember)

http://www.genomic.ch/edena.php

EDNA is high-throughput novel software for de novo assembly of accurate contigs.  It is suitable to characterize a bacterial genome which containing data sets with very short reads of the same length.  This application is based on the classical assembly approach where all overlaps are computed and structured in a graph.  EDNA has two features, exact matching and detection of spurious reads, to improve the assembly of very short sequences: 

There are four steps in this algorithm.

1.  Remove redundant information
  * Significant number of reads are represented several times, it keeps a single copy of each read by removing overlapping  reads – indexing all reads in a prefix tree
  * Ambiguous base symbols are removed because it cannot be handled in the exact matching procedure
  
2.  Overlapping phase
  * All overlaps of a minimum size are computed and an overlap graph is constructed
  
3.  Cleaning and removing transitive and spurious edges
  * Genomic repetitions, sequencing errors, and clonal polymorphisms caused many branching paths that compromise the production of long contigs. There are two steps of graph cleaning process.
  * removing short dead-end paths and fixing bubbles(caused by polymorphisms or by nonexact repetitions in the genomic sequences)
  
4.  All contigs of a minimum size that are unambiguously represented in the graph are provided as output.
























