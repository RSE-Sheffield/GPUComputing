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

	module load libs/caffe/r3/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING-0.1


Create a conda environment to load relevant modules on your local user account and activate it ::

	conda create -n caffe python=3.5
	source activate caffe

You will require ``numpy``, ``boost`` and ``hdf5`` which can all be obtained from the conda repository. ::

	conda install -c anaconda boost=1.61.0
	conda install -c anaconda hdf5=1.8.17
	conda install -c anaconda numpy=1.11.2


You will also need to export the library path of of your conda environment so that caffe can find it ::
	
	export LD_LIBRARY_PATH="/home/<your_username>/.conda/envs/caffe/lib:$LD_LIBRARY_PATH"



Every session afterwards
------------------------

After requesting an interactive session, load the relevant modules and activate your conda environment ::

	module load libs/caffe/r3/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING-0.1
	source activate caffe
	export LD_LIBRARY_PATH="/home/<your_username>/.conda/envs/caffe/lib:$LD_LIBRARY_PATH"

