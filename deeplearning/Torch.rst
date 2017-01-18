Torch on ShARC
==============

Torch is a scientific computing framework with wide support for machine learning algorithms that puts GPUs first. It is easy to use and efficient, thanks to an easy and fast scripting language, LuaJIT, and an underlying C/CUDA implementation.

The following is an instruction on how to setup Torch on your local user account.

Initial setup
-------------

Request an interactive session e.g. ::

	qrshx -l gpu=1 -l rmem=16G -l mem=16G

Or to get the DGX-1 e.g. ::
	
	qrshx -l gpu=1 -l rmem=16G -l mem=16G -P rse -q rse.q 
	
Load the Torch module which also loads anaconda 3.4, CUDA 8.0, cuDNN 5.1 and GCC 4.9.4. ::

	module load libs/torch/nvidia-7/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING
	
(Optional if you plan to interace with python) Create a conda environment to load relevant modules on your local user account and activate it ::

	conda create -n torch python=3.5
	source activate torch



Every session afterwards
------------------------

In the interactive session or your batch script, load the relevant modules and (optionally) activate your conda environment ::

	module load libs/torch/nvidia-7/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING

	#Optional
	source activate torch 
