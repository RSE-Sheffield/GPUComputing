Caffe on ShARC
==============

`Caffe <http://caffe.berkeleyvision.org/>`_ is a deep learning framework made with expression, speed, and modularity in mind. It is developed by the Berkeley Vision and Learning Center (`BVLC <http://bvlc.eecs.berkeley.edu/>`_) and by community contributors.


Initial setup
-------------
The instructions below are for use with python 3.5.

Request an interactive session e.g. ::

	qrshx -l gpu=1 -l rmem=16G -l mem=16G

Or to get the DGX-1 e.g. ::
	
	qrshx -l gpu=1 -l rmem=16G -l mem=16G -P rse -q rse.q 
	
Load the Caffe module which also loads anaconda 3.4, CUDA 8.0, cuDNN 5.1 and GCC 4.9.4. ::

	module load libs/caffe/rc3/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING


(Optionally if you are planning to use the python interface) Create a conda environment to load relevant modules on your local user account and activate it ::

	conda create -n caffe python=3.5
	source activate caffe

You will also require ``numpy`` which can all be obtained from the conda repository. ::

	conda install -c anaconda numpy=1.11.2




Every session afterwards
------------------------

In the interactive session or your batch script, load the relevant modules and (optinally) activate your conda environment ::

	module load libs/caffe/rc3/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING

	#Optional
	source activate caffe
