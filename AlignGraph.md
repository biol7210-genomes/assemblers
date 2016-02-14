#AlignGraph

###Overview:
AlignGraph is a "reference-assisted assembly approach" (1).  Guided by a reference genome of a closely related organism, AlignGraph extends and joins de novo-assembled contigs or scaffolds.  This approach will likely become the default option for many future genome sequencing projects.

###Advantages:
Performance tests show AlignGraph is able to considerably improve the contigs and scaffolds from several assemblers. For example, AlignGraph allowed 28.7–62.3% of the contigs of Arabidopsis thaliana and human to be extended.  This resulted in an increase of the N50 of the extendable contigs by 89.9–94.5% and 80.3–165.8%, respectively (1).

![AlignGraph Steps](/assets/aligngraph.png)

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

###Steps to install AlignGraph:
git clone https://github.com/baoe/AlignGraph 

cp ./AlignGraph/AlignGraph ../../bin 

cd ../ 

wget https://github.com/icebert/pblat/tarball/master 

tar xf master 

cd icebert-pblat-ed0ac17

make 

cp ./pblat ../../../bin 

cd ../ 

wget https://users.soe.ucsc.edu/\~kent/src/blatSrc35.zip 

unzip blatSrc35.zip 

cd blatSrc 

export MACHTYPE=x86_64 

mkdir ~/bin/x86_64 

make -j4 

cp ~/bin/x86_64/blat ../../../bin 

cd ../ 

wget https://github.com/agordon/libgtextutils/releases/download/0.7/libgtextutils-0.7.tar.gz 

tar xf libgtextutils-0.7.tar.gz 

cd libgtextutils-0.7 

./configure --prefix=/data/projects/assembly/ 

make -j4 

make install

cd ../ 

wget https://github.com/agordon/fastx_toolkit/releases/download/0.0.14/fastx_toolkit-0.0.14.tar.bz2 

tar xf fastx_toolkit-0.0.14.tar.bz2 

cd fastx_toolkit-0.0.14 

export GTEXTUTILS_LIBS=-L/data/projects/assembly/lib 

export GTEXTUTILS_CFLAGS=-I/data/projects/assembly/include 

./configure --prefix=/data/projects/assembly/ 

make 

make install

###Preprocessing for AlignGraph
cd aligngraph

fastq_to_fasta -i <(gzip -dc ../../files/M05964_HUY4067A110_TCCGGAGA-TAATCTTA_L002_R1_001_val_1.fq.gz) -o 
./M05964_HUY4067A110_TCCGGAGA-TAATCTTA_L002_R1_001_val_1.fa

fastq_to_fasta -i <(gzip -dc ../../files/M05964_HUY4067A110_TCCGGAGA-TAATCTTA_L002_R2_001_val_2.fq.gz) -o 
./M05964_HUY4067A110_TCCGGAGA-TAATCTTA_L002_R2_001_val_2.fa

cp ../../aroon/reference/GCF_000016465.1_ASM1646v1_genomic.fna.gz ./

gunzip GCF_000016465.1_ASM1646v1_genomic.fna.gz

###Running AlignGraph
screen

AlignGraph --read1 ./M05964_HUY4067A110_TCCGGAGA-TAATCTTA_L002_R1_001_val_1.fa --read2 ./M05964_HUY4067A110_TCCGGAGA-TAATCTTA_L002_R2_001_val_2.fa --contig ./abyss/k99/M05964-contigs.fa --genome ./GCF_000016465.1_ASM1646v1_genomic.fa  --distanceLow 20 --distanceHigh 2000 --extendedContig M05964_extendedContigs.fa --remainingContig M05964_remainingContigs.fa --iterativeMap

###References:
1. Bao E, et al. (2014) AlignGraph: algorithm for secondary de novo genome assembly guided by closely related references, Bioinformatics, 30, i319-i328. (http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4058956/pdf/btu291.pdf)

2. https://github.com/baoe/AlignGraph
