Deep Learning on ShARC
======================

**ShARC (and DGX-1) is currently only available for Computer Science Staff and Students. Please read the guideline below**

Tester's guideline
------------------
- Software requests and error reports can be made by raising an issue on here.

- Evaulation of the hardware requires benchmarks. Please talk to @karmauk to provide benchmarking for your application. Please see the **Benchmarking** section below.

- Help contribute to the documentation process by reporting any mistakes or additional steps needed to get your application running. 

GPU hardware available on ShARC
-------------------------------

- Nodes with Nvidia K80s
- **Nvidia DGX-1** (with 8xP100)


Joining the RSE queue
---------------------

To use the DGX-1 you must join the computer science RSE group and submit jobs to the RSE queue. To joint this group please email `Twin Karmakharm <t.karmakharm@sheffield.ac.uk>`_  or `RSE enquiries <rse@shef.ac.uk>`_.


Logging on to the ShARC system
------------------------------

ShARC uses a similar system to Iceberg so commands for submitting jobs (``qsub``) and requesting interactive sessions (``qrsh, qsh, qrshx`` ) still applies. See the Iceberg `documentation <http://docs.iceberg.shef.ac.uk/en/sharc/hpc/index.html>`_ for further details.

ShARC is located at ``sharc.shef.ac.uk`` so to SSH from a linux system: ::

	ssh -X [your username]@sharc.shef.ac.uk

The ``-X`` option allows for X11 forwarding. This may be necessary if you're planning to use GUI applications e.g. Matlab.
	
Requesting a GPU node (K80)
---------------------------

To request an interactive node with K80 GPUs, type ::

	qrshx -l gpu=1

The ``qrshx`` command will request a node that supports graphical applications and the ``-l gpu=1`` option ensures that you get a node with a GPU. For memory intensive applications you may want to request for more memory by adding something like ``-l rmem=10G`` which asks for 10GB of RAM.

Requesting a DGX-1 node
-----------------------

To request an interactive DGX-1 node, type ::

	qrshx -l gpu=1 -P rse -q rse.q
	
This will put you in a special RSE queue that has the DGX-1.

Submitting jobs
---------------

Jobs can be submitted just like the Iceberg system. First create a job script like so: ::

	#!/bin/bash
	#$ -l gpu=1

	echo "Hello world"
	
In the second line of the script ``#$ -l gpu=1`` you can add more options such as memory request ``-l rmem=10G`` or to be put on the DGX-1 queue ``-P rse -q rse.q``.
	
Run your script with the ``qsub`` command ::

	qsub your_job_script.sh

You can use ``qstat`` command to check the status of your current job. An output file is created in your home directory that captures your script's outputs.


Using DL packages on ShARC
--------------------------

- `Tensorflow <Tensorflow.rst>`_
- `Theano <Theano.rst>`_
- `Torch <Torch.rst>`_
- `Caffe <Caffe.rst>`_

Benchmarking
------------
We are very interested to know how the much additional performance you’re getting by using the system and would also like to build a repository of self-contained examples that can be used to benchmark the system in the future. We will work with you to create benchmarks as mentioned below.

The benchmarking examples should run in various configurations:

- Single and/or multi-CPU on ShARC nodes.
- K80 nodes, for single and multi-GPU.
- DGX-1 (P100) node, single and multi-GPU.

For each benchmarking example there should be:

- Exact copies of the code.
- Detailed build instructions.
- Submission scripts.
- Example data or how we can source the data if needed.
- Results
	- System the code is run on and what configuration.
	- Should be run multiple times to discover variance. 
- Discussion of the results and an explanation of what's actually being run.

Example benchmarking `reports <http://rse.shef.ac.uk/blog/intel-R-iceberg/>`_

- `How each version of R under test got built. <https://github.com/mikecroucher/HPC_Installers/blob/ea4a9f33b705a8cae01841d9c173278fcb486061/apps/R/3.3.1/sheffield/iceberg/intel_15/install_intel_r_sequential.sh>`_
- `The R code that was used <https://github.com/mikecroucher/HPC_Examples/blob/35de11e7c47bc278b15a64fb77c5575b074e1a47/languages/R/linear_algebra/linear_algebra_bench.r>`_
- `Results on Iceberg's Ivy bridge nodes including submission scripts <https://github.com/mikecroucher/HPC_Examples/tree/35de11e7c47bc278b15a64fb77c5575b074e1a47/languages/R/linear_algebra/iceberg_results/intel-ivy>`_






