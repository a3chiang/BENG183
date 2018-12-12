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
ChIA-PET is another method that combines ChIP and pair-end sequencing to analysis the chromtin interaction. It allows for targeted binding factors such as: estrogen receptor alpha, CTCF-mediated loops, RNA polymerase II, and a combination of key architectural factors. on the one hand, it has the benefit of achieving a higher resolution compared to Hi-C, as only ligation products involving the immunoprecipitated molecule are sequenced, on the other hand, ChIA-PET has systematic biases due to ChIP process:
- Only one type of binding factor selected
- Different antibodies
- ChIP conditions


## 2.4.6 Future Applications<a name="246"></a> 
<table>
 <tbody>
    <tr>
        <th>Method</td>
        <th>Targets</td>
        <th>Resolution</td>
        <th>Notes</td>
    </tr>
    <tr>
        <td>3C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0535">[3]</a></td>
        <td>one-vs-one</td>
        <td>~1–10 kb<br></td>
        <td><ul><li>Sequence of bait locus must be known</li><li>Easy data analysis</li><li>Low throughput</li></ul></td>
    </tr>
    <tr>
    <td>4C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0545">[4]</a></td>
    <td>one-vs-all</td>
    <td>~2 kb</td>
    <td><ul><li>Sequence of bait locus must be known</li><li>Detects novel contacts</li><li>Long-range contacts</li></ul></td>
    </tr>
    <tr>
    <td>5C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0550">[5]</a></td>
    <td>many-vs-many</td>
    <td>~1 kb</td>
    <td><ul><li>High dynamic range</li><li>Complete contact map of a locus</li><li>3C with ligation-mediated amplification (LMA) of a ‘carbon copy’ library of oligos designed across restriction fragment junctions of interest
3C</li></ul></td>
    </tr>
    <tr>
    <td>Hi-C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0300">[6]</a></td>
    <td>all-vs-all</td>
    <td>0.1–1 Mb</td>
    <td><ul><li>Genome-wide nucleosome core positioning</li><li>Relative low resolution</li><li>High cost</li></ul></td>
    </tr>
    <tr>
    <td>ChIA-PET <a href="http://refhub.elsevier.com/S0168-9525(15)00063-3/sbref1405">[7]</a></td>
    <td>Interaction of whole genome mediated by protein</td>
    <td>Depends on read depth and the size of the genome region bound by the protein of interest</td>
    <td><ul><li>Lower noise with ChIP</li><li>Biased method since selected protein</li></ul></td>
    </tr>
 </tbody>
</table>

















# Referrence
[1] Schmitt, Anthony D., Ming Hu, and Bing Ren. "Genome-wide mapping and analysis of chromosome architecture." Nature reviews Molecular cell biology 17.12 (2016): 743.<br>

[2] Risca, Viviana I., and William J. Greenleaf. "Unraveling the 3D genome: genomics tools for multiscale exploration." Trends in Genetics 31.7 (2015): 357-372.<br>

[3] Dekker J, Rippe K, Dekker M, Kleckner N. Capturing chromosome conformation. Science 2002;295(5558):1306–11.<br>

[4] Simonis M, Klous P, Homminga I, Galjaard RJ, Rijkers EJ, Grosveld F, et al. High-res- olution identification of balanced and complex chromosomal rearrangements by 4C technology. Nature Methods 2009;6(11):837–42.<br>

[5] Dostie J, Richmond TA, Arnaout RA, Selzer RR, Lee WL, Honan TA, et al. Chromo- some Conformation Capture Carbon Copy (5C): a massively parallel solution for mapping interactions between genomic elements. Genome Res 2006;16(10): 1299–309.<br>

[6] Lieberman-Aiden E, van Berkum NL, Williams L, Imakaev M, Ragoczy T, Telling A, et al. Comprehensive mapping of long-range interactions reveals folding principles of the human genome. Science 2009;326(5950):289–93.<br>

[7] Fullwood, M.J. et al. (2009) An oestrogen-receptor-alpha-bound human chromatin interactome. Nature 462, 58–64.<br>

[8] https://github.com/hms-dbmi/hic-data-analysis-bootcamp/blob/master/HiC-Protocol.pptx.

