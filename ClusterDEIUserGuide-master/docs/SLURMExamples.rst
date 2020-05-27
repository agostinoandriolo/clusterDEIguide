SLURM Job Examples
==================

.. _jobexamples:

MATLAB job
----------
.. _matlabjob:

::
   
  #!/bin/bash
  #SBATCH -J helloMatlab
  #SBATCH -o output_%j.txt
  #SBATCH -e errors_%j.txt
  #SBATCH -t 01:30:00
  #SBATCH -n 1
  #SBATCH -p allgroups
  #SBATCH –mem 10G

  cd $WORKING_DIR   
  #your working directory
  
  srun matlab < example.m

MPI job
-------

.. _mpijob:

::

  #!/bin/bash
  #SBATCH -J hellompi
  #SBATCH -o output_%j.txt
  #SBATCH -e errors_%j.txt
  #SBATCH -t 01:30:00
  # request 32 MPI tasks
  #SBATCH -n 32
  #SBATCH -p allgroups
  #SBATCH --mem 640G
  
  cd $WORKING_DIR   
  #your working directory
  spack load intel-parallel-studio@professional.2019.4
  
  srun ./mphello

.. note::
   ``spack load ...`` initializes the Intel MPI environment and
   is equivalent to ``module load intel-parallel-studio-professional.2019.4-gcc-8.2.1-fnvratt``

OpenMP job
----------

.. _openmpjob:

::

  #!/bin/bash
  #SBATCH -J helloopenmp
  #SBATCH -o output_%j.txt
  #SBATCH -e errors_%j.txt
  #SBATCH -t 01:30:00
  #SBATCH -n 1
  # notice we're using the '-c' option
  # to request for OMP threads
  #SBATCH -c 32
  #SBATCH -p allgroups
  #SBATCH –mem 640G
  
  cd $WORKING_DIR   
  #your working directory
  # set this to what you asked with '-c'
  export OMP_NUM_THREADS=32
  
  srun ./omphello

.. note::
   * ``OMP_NUM_THREADS`` must be set to the same number as the ``-c`` parameter
   * set ``-n`` to 1 if the program uses OpenMP only. If using both MPI and
     OpenMP set ``-n`` to the number of MPI tasks. The total number of slots
     requested, in any case, will be ``n*c``

GPU Job
-------

.. _gpujob:

::

  #!/bin/bash
  #SBATCH -J helloGPU
  #SBATCH -o output_%j.txt
  #SBATCH -e errors_%j.txt
  #SBATCH -t 01:30:00
  #SBATCH -n 1
  #SBATCH -p allgroups
  #SBATCH –mem 640G
  # requesting 1 GPU; set --gres=gpu:2 to use for example two GPUs
  #SBATCH --gres=gpu:1

  cd $WORKING_DIR   
  #your working directory
  
  srun ./GPUhello

.. note::
    In DEI cluster there are currently four servers with GPUs:

    * one server (gpu1) with nine Nvidia Titan Rtx;
    * three servers (runner-04/05/06) with one Nvidia Quadro P2000 each.
   
    Request more than one GPU **only** if your program is capable of using more than one GPU at a time.

.. important::
   DO NOT request GPU if you don't use them!
   To specify a GPU you want to use:
   ::
     #SBATCH --gres=gpu                          Use a generic GPU
     #SBATCH --gres=gpu:titan_rtx                Use Nvidia Titan Rtx GPU
     #SBATCH --gres=gpu:titan_rtx:3              Use for example three Nvidia Titan Rtx GPU
     #SBATCH --gres=gpu:p2000:1                  Use Nvidia Quadro P2000 GPU

Interactive Job
---------------

To run an interactive job using the “interactive” partition, use the command:
 
::
  
 interactive

The interactive command will return an interactive shell to the user. The resources are limited to 1 processor and 3 GB of RAM.
To obtain an interactive shell using the “interactive” partition, the user can also use the following command (one line command)

::
  
  srun --pty --mem=1g -n 1 -J interactive -p interactive /bin/bash 
  
  
To run an interactive job in a specific node (hostname), use the command (one line command)
 
::
     
  srun --pty --mem=1g -n 1 -w hostname -J interactive -p interactive /bin/bash 
  
The interactive shell is active for a maximum of 24 hours.

.. note::
         Interactive jobs should be used ONLY when an real time interaction is needed and/or for tasks having low computation                   burden. Typical examples are the installation of software having an interactive installation procedure, simple file managing/manipulation (e.g. compressing files), etc.

         Do not use the “interactive” partition to run tasks having a long execution time and/or having a high computation burden. These kind of jobs should be executed in the “allgroups” partition.
The use of the “interactive” partition is monitored: jobs that will use this partition in a wrong way will be killed.

.. _InteractivejobwithGPU:

To run an interactive job that use one GPU, use the command (one line command)
 
::
     
  srun --pty --mem=1g -n 1 --gres=gpu:1 -J interactive -p interactive /bin/bash 

To run an interactive job that use for example two specific GPUs, use the command (one line command)
  
::
  
  srun --pty --mem=1g -n 1 --gres=gpu:titan_rtx:2 -J interactive -p interactive /bin/bash 

.. note::
         If the GPUs are already used by other jobs/users, the previous commands will not work.


Singularity Job
---------------

.. _singularityjob:

::

  #!/bin/bash
  #SBATCH --job-name=mysingularity
  #SBATCH --error=opencv.%j.err
  #SBATCH --output=opencv.%j.out
  #SBATCH --partition=allgroups
  #SBATCH --ntasks=1
  #SBATCH --mem=1G
  #SBATCH --time=00:05:00
  
  cd $WORKING_DIR   
  #your working directory
  
  srun singularity exec ./mysingularity.sif python script.py

Singularity job using GPU
-------------------------

.. _singuGpujob:

::

  #!/bin/bash
  #SBATCH -J SingGPU
  #SBATCH -o output_%j.txt
  #SBATCH -e errors_%j.txt
  #SBATCH -t 01:30:00
  #SBATCH -n 1
  #SBATCH -p allgroups
  #SBATCH –mem 640G
  # requesting 1 GPU; set --gres=gpu:2 to use both GPUs
  #SBATCH --gres=gpu:1

  cd $WORKING_DIR   
  #your working directory
  
  srun singularity exec --nv ./tensorflow.sif python script.py

.. important::
   You must request (at least) one GPU and **you must pass the -\\-nv** flag to singularity
