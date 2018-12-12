# 2.4 ChIP Sequencing
1. [Introduction](#241)
2. [Biological Background](#242)
3. [ChIP Sequencing Process](#243)<br>
    3.1. [Workflow](#2431)<br>
    3.2. [Experimental Considerations](#2432)
4. [Computational Analysis](#244)<br>
    4.1. [Workflow](#2441)<br>
    4.2. [Experimental Considerations](#2442)
5. [Current Applications](#245)
6. [Future Applications](#246)


## 2.4.1 Introduction<a name="241"></a>

ChIP sequencing is chromatin immunoprecipitation sequencing. It is a technique that uses a combination of next-generation sequencing technology and current computational analysis to elucidate genomic functions and interactions along the genome. 
Its purpose is to find sites along a genome where proteins interact with DNA. This is important, because with the influx of data, we can look for relationships between regulatory elements and protein binding and genomic regions, which would help the gradual overall understanding of biological flow 

The general workflow entails:
- Fractionating the chromatin - **Crosslink** 
- Shearing DNA into fragments - **Digest or Mechanically Shear**
- Immunoprecipitating desired fragments - **Add protein-specific antibody**
- Purifying fragments - **Reverse crosslinks**
- Sequencing fragments as reads - **Sequence**
- Analyzing reads - **Map reads onto reference genome**

> Upon computational analysis, ChIP sequencing yields peaks, which are genomic areas that, relative to the reference genome, are ChIP-specific, and thus are relevant binding sites between the target protein and DNA. This aids in eventually elucidating the interaction between proteins and DNA and the functions these interactions confer.
> This section gives an overview of the workflow of ChIP sequencing and its experimental considerations, as well as discusses some of its current applications and propose future ones. 

## 2.4.2 Biological Background<a name="242"></a>

To better understand ChIP sequencing, some biological background on genomic features is provided to help clarify the significance of the technology: 
- **DNA structure**: Composed of double-helix strands wrapped around histones into chromatin, which are condensed into tightly-packed nucleosomes, which are subsequently folded into chromosomes. 
- **Protein binding**: Confers biological functions, including but not limited to replication, gene transcription and expression, gene splicing, etc. 
- **Transcription factors**: Proteins that bind to transcription binding sites in order to start gene transcription for gene expression
- **Histone Modifications**: Leads to different effects on transcription based on the combinations of modifications including phosphorylation, methylation, and acetylation. 
- **Enhancers**: Regulatory elements along the genome that alter gene expression; sequential proximity does not always imply physical proximity, as chromosomal structure is folded up rather than linear. 

## 2.4.3 ChIP Sequencing Process<a name="243"></a>

A more detailed look at the workflow and the associated experimental considerations of the ChIP Sequencing process is provided: 

#### Workflow<a name="2431"></a>
A. DNA-binding proteins are crosslinked to DNA with formaldehyde in vivo. When a double strand break is made, a large number of proteins, including those involved with chromatin remodeling, cell cycle arrest, mismatch repair, etc., associate with the break.<br>
B. Isolate the chromatin.<br>
C. Shear DNA along with bound proteins into small fragments.<br>
D. Bind antibodies specific to the DNA-binding protein to isolate the complex by precipitation.<br>
E. Reverse the cross-linking to release the DNA and digest the proteins.<br>
F. Use PCR to amplify specific DNA sequences to see if they were precipitated with the antibody.The DNA can be analyzed using conventional or real time PCR.<br>
G. Sequence and map fragments to a reference genome. The size range of the sonicated DNA can be checked by reversing the crosslinks of the non-immunoprecipitated samples, treating with RNase, and running those fragments on agarose gel. 

#### Experimental Considerations<a name="2432"></a>
Cell harvesting must be done with care and due diligence to ensure best results. Samples must then be prepared for optimal size of fragments and chromatin accessibility. Degree of crosslinking can be adjusted by altering the incubation time with formaldehyde. When it comes to sequencing, the average depth of sequencing coverage must be considered, along with the quality of reads. The accuracy of variant calling is affected by sequence quality, uniformity of coverage and the threshold of false-discovery rate. PCR signal normalization for optimal signal-to-noise ratio must also be considered. When mapping reads, the library complexity and signal-to-noise ratio need to be taken into account. 

## 2.4.4 Computational Analysis<a name="244"></a>
After having mapped the sequenced reads from ChIP sequencing, the results can be analyzed computationally to better understand the biological functions of the various mapped reads in conjunction with their relative locations. 

##### Workflow<a name="2441"></a>
A. Reads are mapped to a reference genome.<br>
B. Peaks are evaluated for read density, revealing where the target protein binds to the DNA a majority of the time.<br>
C. Comparative analyses are carried out to evaluate global similarity, peak conservation, and quantitative changes.<br>
D. Functional analyses are carried out to evaluate peak-to-gene assignment and gene expression. 
E. Sequential analyses are carried out to search for motifs and conserved sequences. 

##### Experimental Considerations<a name="2442"></a>
When mapping reads, it must be decided whether or not to include multiple aligned reads. Allowing them increases the number of usable reads and the sensitivity of peak detection. However, the tradeoff is that the number of false positives may also increase. Normalization for differential analysis in multiplexing is also considered--this can be done via relative-level difference (de novo normalization) or absolute-level difference (spike-in analysis). With regards to peak calling, peak detection generally uses a corresponding input sample to estimate the background distribution at any genomic locus. 

## 2.4.5 Current Applications<a name="245"></a> 
Recent advances of ChIP Sequencing technologies allows for usage of fewer cells, and yield of better resolution. 

Some current applications of this rapidly developing ChIP technology include:<br> 
- **Context-specific co-association identification**: Peak calling is used with relaxed thresholds to obtain candidate regions for investigation. The identified sample peak sets are integrated into co-binding maps and ‘context-specific’ co-associations are identified, which are subsets of peaks binding to different transcription factor sets in other genomic regions.<br>
- **Joint analysis for a de novo genome annotation**: Recently, integrative methods were developed to segment, classify and annotate a whole genome sequence de novo, based on unsupervised machine-learning methods. These methods directly receive all ChIP sample data and analyze them simultaneously, instead of calling peaks and comparing them individually.

## 2.4.6 Future Applications<a name="246"></a> 
With the quickly growing advancements of ChIP sequencing, there is likely to be a growth in directions for science through these developments. 

Possible future directions for ChIP technology include:<br>
- Advancing analysis of nuclear hormone signaling.<br>
- Isolating human transcription factor targets by coupling chromatin immunoprecipitation.<br>
- Chromatin immunoprecipitation for determining the association of proteins with specific genomic sequences in vivo


# Reference
[1] Nakato, R., Shirahige, K. "Recent advances in ChIP-seq analysis: from quality management to whole-genome annotation." Briefings in Bioinformatics. 2016. 18(2): 279-290.<br>

[2] Furey, T.S. "ChIP-seq and Beyond: new and improved methodologies to detect and characterize protein-DNA interactions." Nature Review Genetics. 2012. 13(12):840-852.<br>
