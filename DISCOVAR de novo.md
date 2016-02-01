# DISCOVAR de novo

http://www.broadinstitute.org/software/discovar/blog/?page_id=98

# Overview

DISCOVAR de novo is a variable size genome assembler and variant caller for “next-gen sequencing” data. Currently it takes as input Illumina reads of length 250 or longer — produced on MiSeq or HiSeq 2500 (exclusively) — and from a single PCR-free library. Yet, with adjustments, reads as short as 150bp may work with Discovar de novo, depending on fragment size and other factors. 
The algorithm works by first building the assembly as a graph of unipaths (an unambiguous path). Each read is stitched together as a unipath graph similar to a de Brujin graph. The assembly then undergoes through 2 distinct phases:

*Phase1: Error correction in initial graph:*
* Reads are error corrected
* Pairs are closed
* Pair closues are merged into graph

DISCOVAR starts by correcting errors in the reads, and as part of this process, closing read pairs. To correct a read, DISCOVAR tries to find the 'true friends' of that read, i.e., reads from the same locus on the same chromosome. DISCOVAR uses each read as the “founder” of a stack of “friends”, which consists of a gap-free multiple-sequence alignment among the founder and its friends (exhibited as a matrix of bases, with one row for each read and one column for each position). DISCOVAR seeds alignments on perfect matches to define the initial friend reads associated with the founder (some of which are not true friends). These friends are arranged in a stack, with each friend (or its reverse complement) positioned at a given offset relative to the founder. Posed in this fashion, the central problem of error correction is to remove false friends from the stack. The algorithm scans the stack to find columns in which the founder and a friend both have quality ≥30 but have different base calls. Such friends are declared false and are removed from the stack.

DISCOVAR next finds overlaps between the consensus sequences, allowing for the possibility of more than one overlap. For each overlap, we then merge the left and right stacks, yielding a joint stack, and find its consensus. This 'joint consensus' is a single sequence extending from end to end on the original DNA fragment defining the pair, thus 'closing' the pair.

*Phase2: Optimization of graph:*

* Graph is simplified and improved for accuracy
* Pull apart simple branches
* Pull apart complex branches 
* “Bubble popping” (cleaning up variants)
* Graph reconstruction 
* Orient assembly to reference 

The aim of graph simplification is to remove branches that are not present in the sample (likely artifacts of the laboratory process) and to 'pull apart' the graph that is extend the gaps to align properly with the reference. Briefly, each pair closure may be represented as a path through the graph, or 'closure path'. Graph reconstruction takes the closure paths, each expressed as a sequence of assembly edges, and glues the closure paths together along some (but not all) proper overlaps between them, yielding a new assembly graph.

The resulting assembly is a FASTA file but the actual graph can be viewed as an option to see branches of the graph. Its branches can encode polymorphism, as well as uncertainty arising from technological limitations (laboratory or computational). When DISCOVAR translates the assembly into variant calls, these branches will be visible as alternative paths, all of which are reported by DISCOVAR. In a diploid genome, the most common instance of this phenomenon is a variant, or a phased set of variants, which would be visible as the two branches of a ‘bubble’ in the assembly graph (otherwise removed from final assembly).

