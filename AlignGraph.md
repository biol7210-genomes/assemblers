#AlignGraph

###Overview:
AlignGraph is an assembly software that extends and joins de novo-assembled contigs or scaffolds assisted by a reference genome of a closely related organism. By guiding the assembly process with reference genomes, AlignGraph improves assemblies

Advantage: Since it is a de Bruijn graph-based method, AlignGraph solves limitations associated with heuristic extension methods used in de novo assembly 

###AlignGraph Algorithm Steps:

1. Alignment maps

2. Contig reassembly

3. Graph traversal

###System Requirements:
32-bit or 64-bit machines with Linux operating systems

###Installation:
Bowtie2 and BLAT/PBLAT are required to run AlignGraph

###Inputs:

1. Paired-end DNA reads in FASTA format

2. De novo contigs or scaffolds assembled by:

  * Velvet, ABySS, ALLPATHS-LG, SOAPdenovo, etc.

3. Reference genome from a closely related species

###Usage:

Please see usage section in "Short Manual" section in Reference #2 for input, ouput, and command-line information

###References:
1. Bao E, et al. (2014) AlignGraph: algorithm for secondary de novo genome assembly guided by closely related references, Bioinformatics, 30, i319-i328. (http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4058956/pdf/btu291.pdf)

2. https://github.com/baoe/AlignGraph
