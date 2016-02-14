#SMALT 

  SMALT is a pairwise sequence alignment program for the efficient mapping of DNA sequencing reads onto genomic reference sequences. It uses a combination of short-word hashing and dynamic programming. Most types of sequencing platforms are supported including paired-end sequencing reads.
  
  http://wiki.hpc.ufl.edu/doc/SMALT

##Overview

  Running SMALT involves two steps. First, an index of short words has to be built (smalt index). Then the sequencing reads are mapped onto the reference (smalt map).

  SMALT uses a hash table of words of fixed-length sampled along the ge- nomic reference sequence in the file REFSEQ-FILE at equidistant steps. The sequencing reads in the file READ-FILE (and MATE-FILE) are then mapped against the genomic reference sequences one-by-one.

  First, exactly matching seeds are identified in the reference sequences by looking up the k-mer words of the read in the hash index. Based on these seeds, potentially matching sequence segments are selected for alignment by a Smith-Waterman algorithm.

  The reference sequence file REFSEQ-FILE has to be in FASTA or FASTQ format. The sequencing read file READ-FILE can be in FASTA/FASTQ (default) or in SAM/BAM format.

##Commands

 Index the reference
 
smalt index -k 13 <index_name> <reference_file>

 Mapping
 
smalt map -F fastq -f sam -i 1000 -n 2 -o <mapping_result.sam> <index_name> <query_file_1> <query_file_2>

 Convert the .sam file to .bam file
 
samtools view -bS <mapping_result.sam> > <mapping_result.bam>

 Sort the .bam file
 
samtools sort -o <sorted_result.bam> <mapping_result.bam>

 Index the .bam file
 
samtools index <sorted_result.bam> <index_file>

 Consensus sequence calling
 
samtools mpileup -f <reference_file> -gu <sorted_result.bam> | bcftools call -c -O b -o <output.bcf> 

 Convert the result to .fastq file
 
bcftools view -O v <output.bcf> | vcfutils.pl vcf2fq > <output.fastq>

 Convert the .fastq file to .fasta file
 
seqret -sequence <output.fastq> -outseq <output.fasta>
