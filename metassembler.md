# Metassembler

http://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0764-4

https://sourceforge.net/projects/metassembler/

_______

## General Design

*De novo* assembly integration using local maximas between pairwise unions of alignments to merge areas of conservation and scaffold areas with sparse information. Bowtie mapping of inputs is parsed and local overlap maximas are found using compression–expansion statistics and these overlaps are used to merge assembly `A` and `B`. After creation of the first metassesmbly additional input assemblies are metassembled onto each preceeding metassembly such that the final metassembly is a recursive union of the inputs [`(...((A ∪ B) ∪C ) ∪ D)...) ∪ Z)`]

________

## Metassembly method

![metastage1](/assets/meta1.gif)

Metassembly begins by taking a `primary` and `secondary` assembly and doing the first merge step. This merge is accomplished by `NUCmer` mapping of the secondary assembly to the primary, which is quick mapping step that detects large structural similarities. The `delta` statistics produced by nucmer are used to (temporarily) discard regions with poor or no conservation. 

Next the mate-pair library is aligned to both asesmblies using `Bowtie2` and the resulting insert legnths are used to compute the compression–expansion (CE) statistics used to score regions for inclusion into the metassebly.

Using a Z-score dervied from the CE statistics, a scaffold is built to encompass the "best" knowable assembly based on the imformation present. This is the primary metassembly.

And finally, addional input assemblies are progressively metassembled onto the primary metassembly. Use of additional assemblies (beyond the primary and secondary) improves detection and integration of poorly sequenced regions.



![metareconcile](/assets/meta2.gif)
