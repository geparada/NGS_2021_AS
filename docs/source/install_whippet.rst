.. _whippet:
  
=======================================================
Whippet: a fast and accurate tool for AS quantification 
=======================================================

Whippet is a fast, lightweight and accurate method for quantifying alternative splicing. Given an input gene annotation file on a `GTF format <https://www.ensembl.org/info/website/upload/gff.html>`_, Whippet builds contiguous splice graphs (CSGs) to represent each transcript. Each CSG node represents a non-overlapping exonic sequence, while edges represent splice junctions or contiguous exonic regions. By mapping reads directly to the CSG, Whippet enables a fast annotation-oriented quantification of splicing events.


.. figure:: whippet_model.gif
   :scale: 35 %
   :alt: whippet model

   Figure 1: An overview of Whippet’s computational workflow to quantify alternative splicing events. A. ​Illustration of Whippet’s Node assignment given an example gene annotation with two isoforms. ​B. Representation of the CSG model that would be built given the example gene annotation provided above. ​C. Transcriptome indexing from CSGs generated for each annotated gene. ​D. Read alignment to the indexed transcriptome. E. Alternative splicing quantification through node PSI estimation, which takes into account the full set of RNA-seq reads aligned to edges that connect or exclude the corresponding splicing nodes. This figure was taken from `Whippet's github repository <https://github.com/timbitz/Whippet.jl>`_. For further information about the mode can be found at their publication `Sterne-Weiler et al. 2018 <https://doi.org/10.1016/j.molcel.2018.08.018>`_.


Installation
------------

Whippet was developed as a `Julia <https://julialang.org/>`_ package. During the previous section module (Setup) whe already installed Julia. However, we now need to install Whippet's package. To this end, first we need to enter Julia's interactive mode by just typing: 

.. code-block:: bash

   julia

.. important:: Make sure your ``project`` conda environment is activated. Otherwise julia will not be found in the list of available software. 

Then from this interactive mode we can run

.. code-block:: julia

   Pkg.add("Whippet")

.. note:: 


   This command may take around 30 mins to install. In the mind time we recommend you to read Whippet's paper. Please let us know if you require access.


Once the installation is finished, you can find the path where Whippet was installed by using the following command under Julia's interactive mode:

.. code-block:: julia

   Pkg.dir("Whippet")

Find out how to exit Julia's interactive mode on its `documentation <https://docs.julialang.org/en/v1/manual/getting-started/#:~:text=To%20exit%20the%20interactive%20session,prompts%20the%20user%20for%20input.>`_.


In order to execute Whippet you will need to access its installation path. Inside this path you will find a folder called `bin` where all Whippet's scripts are ready to use! 

.. note:: Make sure you save the path where Whippet is installed on a block note. It will be hard to remember otherwise.

.. important:: To make sure the ``.jl`` scripts have access to write run:

   .. code-block:: bash
      `sudo chmod +x` bin/whippet-*
  




