Singularity Examples
====================

Find below some examples of singuilarity containers built and run on the 
CAPRI platform.

.. _singexamples:

Tensorflow + python packages
----------------------------

Description
"""""""""""

One of the projects required a `tensorflow <https://www.tensorflow.org/>`_ installation plus some other 
softwares for computer vision. Instead of installing everithing system-wide
a singularity file was built by customizing a docker image.

Singularity file
""""""""""""""""

::

   BootStrap: docker
   From: tensorflow/tensorflow:latest-gpu-py3

   %help
      This Singularity definition contains a TensorFlow-gpu installation

   %post
      pip install scipy==1.2.1 six==1.12.0 numpy==1.15.4 pandas==0.24.2 matplotlib==3.0.2
      apt-get -y install libsm6 libxrender1 libxext6 libx11-6
      pip install keras==2.2.4 scikit-learn==0.20.2 opencv-python==3.4.2.17

   %environment
      export LC_ALL=C
   
   %runscript

   %labels
      Author paoloemilio.mazzon

.. note::
   The OS of the built singularity is Ubuntu 18.04 (which is different from the CAPRI one)


Build and run
"""""""""""""

On my PC:

::

   sudo singularity build tflow_opencv.sif Singularity

On CAPRI (only the last line of the slurm script is described):

::

   ...
   ...
   srun singularity exec --nv ./tflow_opencv.sif python script.py 


Reuse and customize a local image
---------------------------------

Description
"""""""""""

A project required a `Torch <https://pytorch.org/>`_ installation to perform som deep learning task.
Since a tensorflow image was available locally we custimized that one instead
of starting from scratch.

Singularity file
""""""""""""""""

.. note::
   The tflow_opencv.sif image is the one described in the `Tensorflow + python packages`_ example.

::

   BootStrap: localimage
   From: ./tflow_opencv.sif

   %post
      pip install torch

   %environment
      export LC_ALL=C

   %runscript

   %labels
      Author paoloemilio.mazzon

Build and run
"""""""""""""

On my PC:

::

   sudo singularity build deeplearn.sif Singularity

On CAPRI (only the last line of the slurm script is described):

::

   ...
   ...
   srun singularity exec --nv deeplearn.sif 
