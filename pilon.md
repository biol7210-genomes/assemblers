# Pilon

https://github.com/broadinstitute/pilon

# Overview
Ostensibly not an assembler but designed as a tool to combine and automate the tasks of correcting of draft assemblies and variant calling.

Pilon requires as input a FASTA file of the genome - either an existing draft assembly or a reference assembly from another strain - along with one or more BAM files of reads aligned to the input FASTA file. It then attempts to make improvements to the input genome using evidence from the reads, including:

* Correcting single base differences
* Resolving repeats using Jump Pairs
* Identifying and aligning small indels
* Fixing larger indel or block substitution events
* Gap filling
* Identification of local misassemblies, including optional opening of new gaps


Pilon then outputs a FASTA file containing an improved representation of the genome from the read data and an optional VCF file detailing variation seen between the read data and the input genome. There is also an option to produce tracks that can be displayed in genome viewers such as IGV and GenomeView.

![Pilon](/aseets/pilon.png)
