#PEAR - Paired-End reAd mergeR
Repository: https://github.com/xflouris/PEAR

*	A memory-efficient and accurate pair-end read merger that can generate reads from both ends of the target DNA fragments.

*	It can assemble 95% of the reads with 35 bp mean overlap, with a false positive rate of 0.004. 

*	It has an extremely low false-positive rate of 0.0003 on datasets where no overlap exists between the two reads. 

*	This assembler is accurate on datasets with: 

  *	short overlaps, and
  
  * DNA target fragment sizes that are smaller than single-end read lengths.
  
*	Highly optimized implementation

*	Currently there is no GUI (Graphical User Interface) for PEAR. IT runs in console more and take a number of mandatory and
optional arguments which affect the process of assembling.

*	The basic command to run PEAR is:

     `./pear -f forward_read.fastq -r reverse_read.fastq -o output_prefix`
 
*	Pear merges reads by maximizing the assembly score (AS) of the read overlap using a scoring matrix that penalizes
mismatches with a negative value  and rewards matches with positive value . 
*	Subsequently, PEAR conducts a statistical test to assess the statistical significance of the merged 
reads. If the merged reads do not pass this test or if the overlap length is smaller than a user-defined 
threshold (based on the expected approximate sequence length in the experiment) the pair of reads will
not be merged. Otherwise, PEAR returns the merged fragment and will also correct errors using the Illumina
quality scores. (http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3933873/)

*	Pear does not require prior information on read length or target fragment size.


