#EPGA2
https://github.com/bioinfomaticsCSU/EPGA2


##Overview

EPGA2 is an updated version from EPGA that does not require vast amounts of memory to handle large genome 
sequences as most assemblers do. It is able to be memory efficienct and still display improved and
higher coverage for contigs and scaffolds. As a first step, read errors are removed to help refine the
precision of De Bruijn Graph and provide less work when assembling the contigs. Secondly, unlike EPGA
which uses a hash table to store K-mers and its counts, EPGA2 has the user define the k-mer size(<32) and 
keeps k-mers that have a frequency greater than one. Lastly, to perfect EPGA2 it parallels the contigs
so that if a portion of a contig has overlapping regions those sections will merge together.

##Algorithm Steps

	1. Error Correction of Read Endings Using BLoom-filter-based Error correction Solution 
	   for high-throughput Sequencing reads (BLESS) 

	2. Uses Disk Streaming of K-mers (DSK) to Count K-mers and Partition Reads from the corrected
       sequences given from BLESS

	3. Uses BCALM to Construct De Bruijn Graph 
		-Stores k-mers in memory as clusters 

	4. Contig Assembly: starts with long nodes from the De Bruijn Graph to find the nodes before
	   and after it 

	5. Parallel Contigs Merging 

	6. Scaffolding: order is determined by paired end reads

	7. Gap Filling 

##System Requirements

	Requires GNU C++ to be pre-installed on ones machine 
  
##Installation

	Copy entire source code to a new main directory
  
##Inputs

	Accepts paired-end reads that are less than 50bp and has a coverage greater than 100
	
##Commands to Run Assembler
	
	BCALM command: ulimit -n 1100
	
	g++ main.cpp -o EPGA -lpthread
	
	perl EPGA.pl library.txt K-merLength ThreadNumber  //kmer length <32
	
##Outputs 

	Two files: contigSetLong.fa and scaffoldLong.fa

##References

http://www.ncbi.nlm.nih.gov/pubmed/26315905

