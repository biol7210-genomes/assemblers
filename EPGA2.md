Overview:

EPGA2 is an updated version from EPGA that does not require large memory to handle large genome 
sequences as most assemblers do. It is able to be memory efficienct and still displays improved
and higher coverage for contigs and scaffolds. It is publicly available at the link listed in 
references.

Algorithm Steps:

1- Error Correction of Reads Using BLESS

2- Uses DSK to Count K-mers and Partition Reads

3- BCALM to Construct De Bruijn Graph

4- Contig Assembly: starts with long nodes to find the nodes before and after it

5- Parallels Contigs Merging 

6- Scaffolding: determined by paired end reads

7- Gap Filling 

System Requirements:

	Requires GNU C++ to be pre-installed on ones machine
  
Installation:

	Copy source code to a new main directory
  
Inputs:

	Accepts paired-end reads that are less than 50bp and has a coverage greater
	than 100

References:

1 - https://github.com/bioinfomaticsCSU/EPGA2

2 - http://www.ncbi.nlm.nih.gov/pubmed/26315905
