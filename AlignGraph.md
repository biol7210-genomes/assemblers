#AlignGraph

###Overview:
AlignGraph is a "reference-assisted assembly approach" (1).  Guided by a reference genome of a closely related organism, AlignGraph extends and joins de novo-assembled contigs or scaffolds.  This approach will likely become the default option for many genome sequencing projects.

###Advantages:
Performance tests show AlignGraph is able to considerably improve the contigs and scaffolds from several assemblers. For example, AlignGraph allowed 28.7–62.3% of the contigs of Arabidopsis thaliana and human to be extended.  This resulted in an increase of the N50 of the extendable contigs by 89.9–94.5% and 80.3–165.8%, respectively (1).

![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

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

3. Reference genome from a closely related organism

###Usage:

Please see usage section in "Short Manual" section in Reference #2 for input, ouput, and command-line information

###References:
1. Bao E, et al. (2014) AlignGraph: algorithm for secondary de novo genome assembly guided by closely related references, Bioinformatics, 30, i319-i328. (http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4058956/pdf/btu291.pdf)

2. https://github.com/baoe/AlignGraph
