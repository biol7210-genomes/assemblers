#!/bin/bash
for i in $(find . -type f  -name '*.fastq.gz' | rev | cut -c 17- | rev | uniq)
do 
/usr/bin/bowtie2 --local -p 3 -x vcholerae -1 ${i}_R1_001.fastq.gz -2 ${i}_R2_001.fastq.gz  -S $i.sam | tee -a bowtie3_align_local.log
echo  ${i}_R1_001.fastq.gz and ${i}_R2_001.fastq.gz processed into  $i.sam | tee -a bowtie3_align_local.log
samtools sort $i.sam $i.sorted | tee -a bowtie3_align_local.log
echo $i.sam sorted into $i.sorted | tee -a bowtie3_align_local.log
bedtools bamtobed -i $i.sorted.bam > $i.bed | tee -a bowtie3_align_local.log 
echo $i.bam converted to $i.bed | tee -a bowtie3_align_local.log
rm $i.sam $i.sorted.bam
mkdir ./alignments
mv $i.bed ./alightments/
done
