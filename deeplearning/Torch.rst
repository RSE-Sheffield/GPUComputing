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
	
Load the relevant modules for ShARC ::

	module load apps/python/anaconda3-4.2.0
	module load libs/cudnn/5.1/binary-cuda-8.0.44
	module load libs/torch/7/binary-TEST

	
Create a conda environment to load relevant modules on your local user account and activate it ::

	conda create -n torch python=3.5
	source activate torch


Install atlas library for your with Torch ::
	
	conda install -c anaconda atlas=3.8.4


Every session afterwards
------------------------

After requesting an interactive session, load the relevant modules and activate your conda environment ::

	module load apps/python/anaconda3-4.2.0
	module load libs/cudnn/5.1/binary-cuda-8.0.44
	module load libs/torch/7/binary-TEST
	source activate torch
