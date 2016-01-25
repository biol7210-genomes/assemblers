# SPAdes 

http://bioinf.spbau.ru/spades 

## General design 

Short reads aligner, using de Bruijn graphs for read assembly and 
conflict resolution. SPAdes standalone was designed for use with 
Illimuna and other short-read technology. It has since been expanded to 
include the ability to align long-reads such as long produced by PacBio 
SMRT systems (hybridSPAdes) and Illunia TruSeq (TruSPAdes). SPAdes was 
designed with small, bacterial genomes in mind and has models for 
chimeric read correction, rearrangements, and other assembler-intriduced 
artifacting. 

## Algorithm 

