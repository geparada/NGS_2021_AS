.. detection_of_differentially_included_nodes
  
==========================================
Detection of differentially included nodes
==========================================

Congratulations if you have reached this point! This is the final step of the analysis :). To achieve the aim of determining the effect of ``TBPH knockout`` you just need to run whippet with the following syntax.

.. code-block:: bash

    julia {path_bin}/whippet-delta.jl -a sample1.psi.gz,sample1.psi.gz,sample1.psi.gz -b sample4.psi.gz,sample5.psi.gz,sample6.psi.gz -o {output_basename}

Where:
    * ``{path_bin}`` needs to be replaced by the path to find the ``whippet-delta.jl`` script.
    * ``-a``/``-b`` are input a comma-separated list the ``.psi.gz`` files obtained for each condition.
    * ``{output_basename}`` should be replaced by any desired output name.


.. admonition:: Challenge 3

    Run the this command over your samples! 


.. admonition:: Challenge 4

    Find on `Whippet's <https://github.com/timbitz/Whippet.jl>`_ documentation about the obtained results. Particularly focus on interpreting the last file obtained ``.diff.gz`` file. According to this, answer the following questions:

        1. How many differentially included nodes did you find? (See documentation to find recommendations from the authors)
        2. How many of them might be biologically relevant based on DeltaPsi obtained values?
        3. What type of alternative splicing node are the ones found significantly different and biologically relevant ``TBPH knockout``?


.. admonition:: Challenge 5

    Important part of the job as bioinformatician is to inspect the obtained results using a genome browser. Use the IGV to generate `sashimi plots <https://software.broadinstitute.org/software/igv/Sashimi>`_ that allow you to evaluate the changes if the changes in splicing after ``TBPH knockout`` looks convincing.