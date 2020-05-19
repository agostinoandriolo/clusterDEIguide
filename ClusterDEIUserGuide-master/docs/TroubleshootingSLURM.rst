SLURM Troubleshooting
---------------------

.. _slurmrtrouble:

  * Why is my job not running?

     The answer depends on a lot of factors, but in many cases the job is put in
     a PENDING state if there is not enough free resources for it.

  * How can I get my job start earlier?

     If there are enough free resources, your job will start in few seconds. If the
     machine is intensively used by other users (of by your jobs), Slurm will
     execute your job as soon as there are enough free resources. Make sure
     you only request the resource you need: the more you ask, the longer you
     and other users will wait.

  * Why was my job killed?

     The answer depends on a lot of factors, but in most cases the job is killed
     if it exceeds the resource limit specified in the job file (run time and/or
     memory).
