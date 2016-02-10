#ABySS (Assembly By Short Sequencing)

-Amounts of data generated from large-scale sequencing projects

-3.5 billion paired-end reads from the genome of an African male publicly released by Illumina

Algorithmic Approach:
1. All possible substrings of length k (termed k-mers) are generated from the sequence reads.
The k-mer data set is then processed to remove read errors and initial contigs are built

2. Mate-pair information is used to extend contigs by resolving ambiguities in contig overlaps

Evaluation of ABySS Performance:
-Simulated data

-Experimental sequence data

-Comparison of short read assemblers

-Polymorphic and novel human sequence identified in the assembled experimental data

Reference: http://www.bcgsc.ca/platform/bioinfo/software/abyss

