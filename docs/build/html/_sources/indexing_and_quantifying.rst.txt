.. indexing_and_quantifying

===============================================
Transcriptome guided quantification of isoforms
===============================================

The aim of the analysis of this project is to find differentially included splicing nodes. This can be done three "simple" steps:

    1. Transcriptome indexing 
    2. Quantification
    3. Detection of differentially included nodes


Building a transcriptome index
============================== 

Instead of the classical approach of mapping reads to the genome and then quantifying gene expression, Whippet's quantification is performed considering the gene annotation coordinates and features. These are usually stored as a GTF file and Whippet takes these as input to generate transcript models. In order to generate such models, one needs to build an index based on the GTF and Genomic sequences (fasta).


.. admonition:: Challenge 1

    One of the key skills required to learn bioinformatics is to understand the documentation from tools deposited on GitHub or other popular software archives. In order to index the transcriptme using Whippet read the official documentation from Whippet's `GitHub <https://github.com/timbitz/Whippet.jl>`_. What you need to know is on section 2A. Use the files available at ``Data/dm6/``.


.. tip:: ``dm6.ensGene.gtf.gz`` corresponds to a GTF file, while ``dm6.fa.gz`` is the `release 6 <https://www.ncbi.nlm.nih.gov/assembly/GCF_000001215.4/>`_of  `Drosophila melanogaster`'s genome.

.. important:: To execute any of the whippet commands you should locate the ``/bin`` folder inside the directory where Whippet was installed.

  

Quantifying splicing nodes and transcripts
==========================================

For the quantification step ``bin/whippet-quant.jl`` is used. To find more about this command use:

.. code-block:: bash

    julia bin/whippet-quant.jl --help


For this, one could deduce that the general command to run this step is by using:

.. code-block:: bash

    julia bin/whippet-quant.jl sample.fastq.gz -o out_dir/sample --sam > sample.sam


Where `out_dir/sample` is the base name for the output (five files will be generated) and sample.sam is an optional output that whippet provides when the ``--sam`` flag is given.

.. admonition:: Challenge 2

    Apply the general syntax explained above to quantify the 6 samples you downloaded (``.fastq.gz`` files). You could write a bash script to do this.
