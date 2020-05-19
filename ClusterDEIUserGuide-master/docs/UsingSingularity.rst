Using Singularity
-----------------

.. _whatsingularity:

Singularity is a *container* technology. It allows the user to create a
container (just like `Docker <https://docker.com>`_ ones) where all the
needed software can be autonomously managed. By *software* we mean that
almost everithing, from the operative system up, can be customized and
run regardless the hosting OS.

Why singularity?
^^^^^^^^^^^^^^^^

  * Singularity can run your choice of operative system;
  * Singularity can import your Docker images without superuser privileges 
    and without Docker installed;
  * Singularity is a good way to share your code;
  * Configure on your personal PC; run in the CAPRI environment.

Singularity workflow
--------------------

.. important::
   This is not a Singularity tutorial. Please read the `Singularity user guide <https://sylabs.io/guides/3.4/user-guide/>`_
   first if you're starting from scratch.


You tipically build the singularity file on your PC. The singularity image can 
then be transferred to CAPRI and run there.

Building the singularity image
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Starting from a `Singularity file <https://sylabs.io/guides/3.4/user-guide/definition_files.html>`_
you can work interactively on a singularity container:

::

   sudo singularity build --sandbox tmpdir/ Singularity

or you can build a writable container

::

   sudo singularity build --writable container.img Singularity

You can start from an already built image from the `singularity hub <https://singularity-hub.org/>`_

::

   sudo singularity build container.img shub://vsoch/hello-world

or importing directly a `Docker image <https://hub.docker.com/>`_

::

   sudo singularity build container.img docker://ubuntu


Running the singularity image locally
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can run / modifiy your container locally on your PC until satisfied. To test run your
image you can use

::

   singularity run container.img

or, to access the container interactively

::

   singularity exec container.img


Running the singularity image on CAPRI
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Once copied on the CAPRI platform the singularity image can be executed with a slurm
job file like the one described in :ref:`Singularity job example <singularityjob>`
