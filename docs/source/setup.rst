.. setup:

===== 
Setup
=====

The life of a bioinformatician is not as easy as some may think. A large amount of time is spent trying to install software and reproduce other researcher's methods. In this section, you will download all the software and necessary data to conduct alternative splicing analysis using RNA-seq. The following steps will enable you to do this.

Installing Conda
================

Conda is an open-source package management system which enables the installation of a variety of different computational tools. To install conda, please follow this `link <https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh>`_ and download it inside your ``~/Downloads`` folder. To start installing conda open the terminal and execute the following command:

.. code-block:: bash

    bash ~/Downloads/Miniconda3-latest-Linux-x86_64.sh

Follow the instructions displayed in the command line by pressing the ``Enter`` key and writing ``yes`` when required by the installer. If the installation is successful, you will receive the following message in the prompt.

.. code-block:: bash

    Thank you for installing Miniconda3!

Moreover, if you list content inside the home directory, you will see a ``miniconda3`` folder. To make sure conda has the rights to write files on this directory and install software, please type the following commands:

.. code-block:: bash


    sudo chmod 755 -R /home/manager

.. note::

    The command above will require your password, which is the same than your user name. To check your user name insert ``whoami`` in the terminal.

Finally, to test everything is in place, execute the following command, which will instruct conda to update itself:

.. code-block:: bash

   conda update -n base -c defaults conda


Installing software dependencies
================================

To install the software necessary for this project, we will first create a virtual environment, and we will install the software dependencies within this virtual environment. This will avoid interfering with the other software installed in the VM. To create a virtual environment called ``project`` that contain all the necessary software for this project please execute the following command:


.. code-block:: bash

   conda create --name project sra-tools julia=0.6.1=blas_openblas_200 gcc_linux-64


.. note::

    This command may take some minutes to resolve the dependencies, when is finished correctly, it will require you to accept the changes by inserting the ``y`` key.


To execute any of the commands related to this project, we first need to activate the environment, ``project``, that we just created.

.. code-block:: bash

   conda activate project

.. Important::

    If you open a new terminal this environment will not be active by default, therefore would not be able to access the required software unless you activate the ``project`` environment again. Moreover, to inactivate the environment you can use the `deactivate` conda command:

    .. code-block:: bash

        conda deactivate project


    
Downloading the data and understanding the study design
=======================================================

Before starting developing this project we will need to download all the the necessary data. Similarly to the sofware we installed, the data is all available online.

Cloning github repository of this project
-----------------------------------------

The first step to get the data is to clone the git repository for this project. To this end, create a new directory (using ``mkdir``) called ``Project`` and move into it (using ``cd`` command). Then, copy the following command in the terminal:

.. code-block:: bash

   git clone https://github.com/geparada/NGS_2021_AS


This command will make a clone of the repository in your local computer. After the command finishes running, a new folder (called ``NGS_2021_AS``) will be created at the directory where you executed the command. Change into this directory.

.. admonition:: Do you want to know more?

    In addition to the data, this repository also includes the documentation you are currently reading. To get an idea of how this type of documentation can be created, visit this `link <https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html>`_. 


The data we will be using is available from the ``NCBI archive``. To download it, we are going to use fastq-dump, which is part of `SRA-Tools  <https://ncbi.github.io/sra-tools/>`_. To efficiently get the data we are going to execute a `bash` script which will execute fastq-dump to download some RNA-seq samples. To run this script, change directory (using ``cd`` command) to ``Data/samples/`` and execute the following command:

.. code-block:: bash

   bash download.sh &

.. Note:: This command will download four ``fastq.gz`` files. The character ``&`` will enable us to run this command in the background and still have access to the terminal. Depending on the internet connection this may take between 20-50 minutes. Use ``ls -l`` to check the progress in that ``Data/samples/``. 


Exercise 1
^^^^^^^^^^
Take a look inside the ``download.sh`` script and investigate the commands used.

A) Go to `SRA <https://www.ncbi.nlm.nih.gov/sra>`_ and find the project you are downloading data from. Which organism are the samples come from? 

.. hint:: Identify the accession code of one of the files and use the search button.

B) Check the metadata of the study and identify the experimental condition of every sample you are currently downloading. 

.. hint:: Check the Study information and click on ``All runs``


Study design
------------

In this project, we are going to study the effects on alternative splicing resulting from TBPH loss of function (LoF). For more details about the study please check the information of the study and its corresponding publication. 


Exercise 2
^^^^^^^^^^
Ops! the bioinformatician who wrote the script forgot to include two samples to study the effect of TBPH knockout! Before continuing please check all the samples available on SRA, identify the missing TBPH-mutant samples, and download them to ``Data/samples``

.. hint:: Check the ``Data/samples/download.sh`` file and the run metadata available on ``SRA``.

.. DANGER::

    Do not execute ``data/samples/download.sh`` again, otherwise you will re-write the downloaded data. But if this happened, do not panic. Re-writing files is a mistake that is far more frequent that one would expect.  

Exercise 3
^^^^^^^^^^

To make sure you got the final result, your collaborator sent you the expected sizes from the files you are downloading.


.. code-block:: text

    total 2728888
    -rw-r--r--  1 gp7  1535   221M 01 Jan 14:14 SRR363940.fastq.gz
    -rw-r--r--  1 gp7  1535   330M 01 Jan 14:09 SRR363938.fastq.gz
    -rw-r--r--  1 gp7  1535   155M 01 Jan 14:02 SRR363935.fastq.gz
    -rw-r--r--  1 gp7  1535   226M 01 Jan 13:59 SRR363932.fastq.gz
    -rw-r--r--  1 gp7  1535   133M 01 Jan 13:54 SRR363931.fastq.gz
    -rw-r--r--  1 gp7  1535   240M 01 Jan 13:52 SRR363927.fastq.gz
    -rw-r--r--  1 gp7  1535   180B 01 Jan 13:41 download.sh


Which command do you think your collaborator used to generate this? Use the same command to check if the data you downloaded matches. If you are still downloading them, please continue with the following modules.








