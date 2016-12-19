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

	module load libs/torch/7/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING-0.1
	
Create a conda environment to load relevant modules on your local user account and activate it ::

	conda create -n torch python=3.5
	source activate torch

Install atlas library for your with Torch ::
	
	conda install -c anaconda atlas=3.8.4


Every session afterwards
------------------------

After requesting an interactive session, load the relevant modules and activate your conda environment ::

	module load libs/torch/7/gcc-4.9.4-cuda-8.0-cudnn-5.1-conda-3.4-TESTING-0.1
	source activate torch
