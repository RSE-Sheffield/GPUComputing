Deep Learning on ShARC
======================

**ShARC (and DGX-1) is currently only available for testing purposes. Please read the guideline below**

Tester's guideline
------------------

- The system is currently provided for testing purposes and configurations will change as we perform tests and finalise the details. This can sometimes cause instability in the system. We will try to warn you ahead of any major changes or planned outages. 

- Software requests and error reports can be made by raising an issue on here.

- Provide benchmarking for your application. We are very interested to know how the much additional performance you’re getting by using the system. Comparisons between running it on the CPU, your own GPU, the K80 nodes and the P100 nodes (DGX-1) with single and multi-gpu setup will be very useful.

- Help contribute to the documentation process by reporting any mistakes or additional steps needed to get your application running. 

GPU hardware available on ShARC
-------------------------------

- Nodes with Nvidia K80s
- **Nvidia DGX-1** (with 8xP100)


Logging on to the ShARC system
------------------------------

ShARC uses a similar system to Iceberg so commands for submitting jobs (``qsub``) and requesting interactive sessions (``qrsh, qsh, qrshx`` ) still applies. See the Iceberg `documentation <http://docs.iceberg.shef.ac.uk/en/sharc/hpc/index.html>`_ for further details.

ShARC is located at ``sharc.shef.ac.uk`` so to SSH from a linux system: ::

	ssh [your username]@sharc.shef.ac.uk
	
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
	
Then run your script with the ``qsub`` command ::

	qsub your_job_script.sh

You can use ``qstat`` command to check the status of your current job. An output file is created in your home directory that captures your script's outputs.


Using DL packages on ShARC
--------------------------

- `Tensorflow <Tensorflow.rst>`_
- `Theano <Theano.rst>`_
- `Torch <Torch.rst>`_
- **Caffe** coming soon





