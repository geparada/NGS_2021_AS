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

    julia /home/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-index.jl --fasta mm10.fa.gz --gtf mm10.ensGene.gtf.gz --index mm10.index

    julia /home/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E10.5_rep1*.fastq.gz) --force-gz  -x mm10.index.jls -o midbrain_E10.5_rep1
    julia /home/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E10.5_rep2*.fastq.gz) --force-gz  -x mm10.index.jls -o midbrain_E10.5_rep2
    julia /home/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E14.5_rep1*.fastq.gz) --force-gz  -x mm10.index.jls -o midbrain_E14.5_rep1
    julia /home/gp7/miniconda/envs/julia_0.6.1/share/julia/site/v0.6/Whippet/bin/whippet-quant.jl <( cat  midbrain_E14.5_rep2*.fastq.gz) --force-gz  -x mm10.index.jls -o midbrain_E14.5_rep2

However, as most of bioinformaticians, he was a bit lazy to finish the job and he asked you to do it instead! He sent you the ``.psi.gz`` he obtained. You can find these files at ``Data/Advanced/``.

.. note:: As a general rule ``rep`` indicates biological replicates and ``L`` technical replicates, which are samples that were extracted from the same animal but sequenced on different runs. Thus, on this script technical replicates that correspond to the same biological sample are pooled during the quantification step (check ``--force-gz`` parameter on Whippet's documentation) 


.. admonition:: FINAL CHALLENGE

    Take back control of this splicing project and finish it up by taking the following steps:

        1. Run the last necessary command to detect the alternatively spliced events associated to the embryonic development of mouse midbrain (between E10.5 and E14.E)
        2. Use your bash skills to calculate how many differentially spliced nodes you detected between these conditions. How many of each splicing node type did you detect?
        3. Run the ``Data/Advanced/download_bam.sh`` script to get at least one ``BAM`` file representing each embryonic stage and use these to generate sashimi plots. Find some examples to show in your presentation.
        4. Generate a non-redundant list of genes with highly variable Core Exon nodes (CE) that has an absolute ``DeltaPsi`` value of at least 0.3 and ``Probability`` greater than 0.9. Use this list to perform `gene ontology analyses <http://bioinformatics.sdstate.edu/go/>`_ and protein-protein interaction networks analyses with `STRING <https://string-db.org/>`_ (if you reach this point please seek the attention of the instructor in charge of this project).



