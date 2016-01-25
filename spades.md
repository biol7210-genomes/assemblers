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

High level view of SPAdes assembly:

1.  Assembly graph construction with multisized de Bruijn graphs (dBG) and bulge resolution 

2.  Integration of Pair-end data with dBG-derived paths to determine genomic distance

3.  Paired assembly graph

4.  Contig reconstruction

## Algorithm 

1.   

SPAdes derives its assembly graph construction model ("bulge corremoval") from two previously published methods. dBG assemblers make use of kmers to split reads for assembly, however kmer size is typically a user-provided constraint and chosing the "wrong" size can result in poor assemblies. SPAdes utilizes multisized de Bruijn graph which integrate pairs of bikmers over a predefined range of kmer sizes, producing assembly graph DB\*(*Reads,k*). Graph bulges are resolved by random mixing of DB\*(*Reads,k*), DB\*(*Reads,k'*),..., and chosing the least tangled combination of split-paths.  

2.   

![Stage 2](/assets/spades_stage2.jpeg)

3.   



4.   