#EPGA2
https://github.com/bioinfomaticsCSU/EPGA2


##Overview

EPGA2 is an updated version from EPGA that does not require vast amounts of memory to handle large genome 
sequences as most assemblers do. It is able to be memory efficienct and still display improved
and higher coverage for contigs and scaffolds. As a first step, read errors are removed to help refine
the precision of De Bruijn Graph and provide less work when assembling the contigs. 

##Algorithm Steps

	1. Error Correction of Reads Using BLESS

	2. Uses DSK to Count K-mers and Partition Reads

	3. BCALM to Construct De Bruijn Graph

	4. Contig Assembly: starts with long nodes to find the nodes before and after it

	5. Parallels Contigs Merging 

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

