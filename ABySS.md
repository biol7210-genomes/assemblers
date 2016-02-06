The ABySS algorithm proceeds in two stages. First, all possible substrings of length k (termed k-mers) are generated from the sequence reads. The k-mer data set is then processed to remove read errors and initial contigs are built. In the second stage, mate-pair information is used to extend contigs by resolving ambiguities in contig overlaps.

A common shortcoming of the available tools is their inability to efficiently assemble vast amounts of data generated from large-scale sequencing projects, such as the sequencing of individualhuman genomes to catalog natural genetic variation. To address this limitation, ABySS is developed.

The developers using simulated data to test it and find that misassembled contigs represent less than 1% of the total contigs and less than 1% of the genome in both assemblies using error-free data. 

For the experimental sequence data, a small portion of the 2.76 million contigs (0.08%) they observe significant alignment inconsistencies. However, the observed frequency of such contigs is within range of the 0.04% and 0.10% of contigs with these types of anomalous alignments that we observed in the assemblies with simulated perfect-coverage data and simulated ampled data, respectively, indicating that the majority of these are likely to be incorrectly assembled contigs.
