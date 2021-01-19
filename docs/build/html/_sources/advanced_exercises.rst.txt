.. advanced exercises


==================
Advanced exercises
==================


The number of genes that undergoes through alternative splicing is known to be substantially higher than invertebrates or other metazoans. Moreover, the biggest set of regulated AS events are associated with neuronal tissues and are particularly relevant during development of the brain. Therefore, you and your bioinformatician friend were excited to try out Whippet with some of the data that is available at `ENCODE <https://www.encodeproject.org>`_. You decided that would be interesting to process RNA-seq samples from midbrain to detect alternative splicing events between E10.5 and E14.5. To this end,  your bioinformatician friend wrote the following script in bash:


.. code-block:: bash


    #!/bin/bash

    wget https://www.encodeproject.org/files/ENCFF099UUS/@@download/ENCFF099UUS.fastq.gz -O midbrain_E10.5_rep1_L01.fastq.gz
    wget https://www.encodeproject.org/files/ENCFF059FUK/@@download/ENCFF059FUK.fastq.gz -O midbrain_E10.5_rep1_L02.fastq.gz
    wget https://www.encodeproject.org/files/ENCFF052VGB/@@download/ENCFF052VGB.fastq.gz -O midbrain_E10.5_rep2_L01.fastq.gz
    wget https://www.encodeproject.org/files/ENCFF819ZTA/@@download/ENCFF819ZTA.fastq.gz -O midbrain_E10.5_rep2_L02.fastq.gz

    wget https://www.encodeproject.org/files/ENCFF156BSL/@@download/ENCFF156BSL.fastq.gz -O midbrain_E14.5_rep1_L01.fastq.gz
    wget https://www.encodeproject.org/files/ENCFF421QJA/@@download/ENCFF421QJA.fastq.gz -O midbrain_E14.5_rep1_L02.fastq.gz
    wget https://www.encodeproject.org/files/ENCFF499UQZ/@@download/ENCFF499UQZ.fastq.gz -O midbrain_E14.5_rep2_L01.fastq.gz
    wget https://www.encodeproject.org/files/ENCFF093YSD/@@download/ENCFF093YSD.fastq.gz -O midbrain_E14.5_rep2_L02.fastq.gz

    wget https://hgdownload.soe.ucsc.edu/goldenPath/mm10/bigZips/mm10.fa.gz -O  mm10.fa.gz
    wget https://hgdownload.soe.ucsc.edu/goldenPath/mm10/bigZips/genes/mm10.ensGene.gtf.gz -O mm10.ensGene.gtf.gz

    julia /lustre/scratch117/cellgen/team218/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E10.5_rep1*.fastq.gz) --force-gz  -x mm10.index.jls -o midbrain_E10.5_rep1
    julia /lustre/scratch117/cellgen/team218/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E10.5_rep2*.fastq.gz)  --force-gz  -x mm10.index.jls -o midbrain_E10.5_rep2
    julia /lustre/scratch117/cellgen/team218/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E14.5_rep1*.fastq.gz)  --force-gz  -x mm10.index.jls -o midbrain_E14.5_rep1
    julia /lustre/scratch117/cellgen/team218/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E14.5_rep2*.fastq.gz)  --force-gz  -x mm10.index.jls -o midbrain_E14.5_rep2

However, as most of bioinformaticians, he was a bit lazy to finish the job and he asked you to do it instead! He sent you the ``.psi.gz`` he obtained. You can find these files at ``Data/Advanced/``.

.. note:: `rep` indicate biological replicates and `L` technical replicates. On this script technical replicates are pooled during the quantification step. 


.. admonition:: FINAL CHALLENGE! 

    Take back control of this splicing project and finish it up by taking the following steps:

        1. Run the last necessary command to detect the alternatively spliced events associated to the embryonic development of mouse midbrain (between E10.5 and E14.E)
        2. Use your bash skills to calculate how many differentially spliced nodes you detect between these conditions and how many differentially spliced nodes of each type you could detect.
        3. Run the `Data/Advanced/download_bam.sh` script to get at least one ``BAM`` file representing each embryonic stage and use these to generate sashimi plots that enable you to inspect the nodes splicing nodes that change the most.
        4. Extract the names of genes in which you detected confident alternative splicing changes and perform gen ontology analyses. 



