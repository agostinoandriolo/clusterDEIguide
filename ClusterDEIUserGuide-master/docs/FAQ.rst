8. Frequently Asked Questions
==============================
.. |br| raw:: html

     <br>


**Where can I write my temporary data?**

The nodes of the cluster have a scratch directory (/ext). This is writable by everyone and is the ONLY place to save temporary files.

**Where can I write my permanent data?**

If there is a need to write a large amount of data permanently and this exceeds the quota of the personal home, you should contact the research group you work with to have access to their space on the NAS or, if this is not possible, open a ticket motivating the need to have a greater share of space on your home.

**How can I select a specific GPU?**

If the selection via the --gres option leads to an ambiguity (for example the choice gpu:rtx which indicates both the Titan RTX and the RTX 3090) then it is necessary to clarify the name of the machine equipped with the type of GPU desired . If this were for example the machine named gpu1, then the option to add would be: -w gpu1 or --nodelist=gpu1.
The downside of using this option is that you will probably have to wait some time before that particular machine is available to run the code.

**What should I do if I realize that I need more time to carry out my jobs than initially estimated or if I find that I have to exceed the maximum duration foreseen?**

In these cases, a report must be made to the IT Services via the helpdesk portal, which can be reached at the site https://www.dei.unipd.it/helpdesk, providing an estimate of the time needed to complete the jobs, i.e. how many days must be extended with respect to what was specified during the launch of the same.

**I'd like to run my jobs on a different machine than the one I've been assigned, but without choosing a particular machine. How can it be done to exclude it from those that can be assigned to me?**

A specific machine can be excluded using the --exclude option. Assuming that the runner to avoid is number 01, the option becomes: --exclude=runner-01.

**How can I install a package that I need and which I discovered is not present on the Matlab installation that is being made available?**

In this regard there are two possibilities.

Solution 1:
connect to login.dei.unipd.it via ssh enabling X11 forwarding (with the -X option), then open an interactive graphical session on the cluster with the "sinteractive" command and launch matlab. Continue with the graphical interface.
Solution 2:
open an interactive session on the cluster with the "interactive" command and launch matlab textually. Then run the following commands replacing the example path with that of the downloaded file:
toolboxFile = 'C:\Downloads\My toolbox.mltbx';
agreeToLicense = true;
matlab.addons.install(toolboxFile,agreeToLicense)

**How can an environment like Anaconda be used in the execution of jobs?**

You need to run the source command followed by the path before running the actual code.
You can then experiment with an interactive job by connecting with ssh to login.dei.unipd.it and then giving the "interactive" command. This opens a shell in the first free runner.

**How can I install persistently missing packages on Apptainer (also known as Singularity)?**

There are two ways to achieve this:
    1. you create a personal Apptainer image complete with everything you need and work on it. Bear in mind that it could take up several GB of space;
    2. a Python virtual environment (Python virtualenv) is created in the personal space and the various installations are made inside it, perhaps with the pip install command. With the command source it will then be possible to recall the /bin/activate of the environment.
    
*Is it possible to map a non-home workbook to Apptainer?*

The home is automatically mapped inside the container. If you want to map the directory to, say, /my_dir you need to add the --bind /my_dir option:
singularity exec --bind /my_dir

**I can't run an externally compiled program on the compute cluster. How do I solve?**

The binaries must necessarily be compiled with the libraries present in the cluster. So if some binaries are not recognized, you have to log in to login.dei.unipd.it and type the interactive command which opens a shell on one of the servers in the cluster. At this point you need to recompile the programs.

**Is a GPU allocation exclusive or if enough memory is left over is the GPU also shared with other jobs? So if a GPU is requested is it possible to specify the associated memory needed?**

Each allocation (CPU, RAM, GPU) is exclusive for the job, so the fact of not fully exploiting the internal memory of a GPU does not lead to being able to share it among multiple jobs.

**I need to have parallel tasks to work with a parfor loop in Matlab. How do I behave?**

Assuming you want to have 10 workers, you will need to ask for a task and a number of CPUs equal to 11, so as to dedicate one to the Matlab process and 10 for the useful work of the parallel tasks:
#SBATCH --ntasks 1
#SBATCH --cpus-per-task 11

**Is it necessary to be user "root" to build the Apptainer image?**

With Apptainer you can build the image without having to be a "root" user or in the "sudoer" list.
