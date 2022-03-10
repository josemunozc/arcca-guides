Running Jobs
============

What is the Job Scheduler on Hawk?
-----------------------------------
SLURM, developed by SchedMD, is the job scheduler used on Hawk. 
Advice on using and setting up job scripts are provided in the ARCCA *Quick
Start User Guide*.

How do I run a job on Hawk?
----------------------------
A job is submitted with a command called ``sbatch``. The job can be submitted
either directly from the command line or using a job script that contains
directives which ``sbatch`` can understand. For example a job script 
(myjob.q) can contain::

  #SBATCH --partition=htc
  #SBATCH --nnodes=1
  #SBATCH --ntasks=1 
  #SBATCH --ntasks-per-node=1
  #SBATCH --account=scwXXXX

The job (or batch job) would then be submitted with::

  $ sbatch myjob.q

Depending on the available resources on Hawk the job will either run
immediately or be held in a queue until the resources are available (such as a
number of CPUs).

Where do I find the output from my job?
---------------------------------------
When a job is run it is important to know where it was run on the system, we
recommend jobs are run within the /scratch filesystem. SLURM also writes the
output which normally would go to the screen (the standard output and error)
to a file. This is defined within the job directives, for example to save the
standard output and error into files output.txt and error.txt in the directory
you submitted the job, the directives would be::

  #SBATCH –o output.txt
  #SBATCH –e error.txt

These output files, unless explicitly directed elsewhere, will be written to
the directory from which the job was submitted from (i.e. the directory where
the ``sbatch`` command was issued).

Is there a way to get status information on the nodes in the cluster?
---------------------------------------------------------------------
The command ``sinfo`` can be used to find the status of the nodes within the
queues on Hawk.

My job terminates without any message or warnings.
--------------------------------------------------
If you know the SLURM job id number you can find out information using::

  $ scontrol show job <jobid>

for recently ended jobs (a few minutes). More generally, you can use::

  $ sacct -j <jobid>

``sacct`` allows you to query different information fields, for example::

  $sacct -j <jobid> --format=JobID,User,JobName,Partition,Account,AllocCPUS,\
  State,ExitCode,NNodes,NCPUS,CPUTime,ReqMem,TotalCPU,Elapsed,Submit

See sacct manual information for all the different field options.

If it is not clear as to why the job failed please `contact us`_.

My program, which use to work, stopped working.
-----------------------------------------------
ARCCA tries to reduce the impact of maintenance work on Hawk but occasionally
the operating system or software modules can change. This may impact some
software in unexpected ways. If the code is compiled by the user then please
try recompiling the program which may link the new locations of libraries.

If the software is provided by a module please report the error to ARCCA.

Can I get email notification when a job finishes?
-------------------------------------------------
A SLURM directive provides an option to email the user when the job reaches a
certain status such as completing. The SLURM directives are::

  #SBATCH –-mail-type=BEGIN,END,FAIL
  #SBATCH --mail-user=<user@cardiff.ac.uk>

``BEGIN``, ``END`` and ``FAIL`` instructs SLURM to send email when the job
starts execution, finishes successfully and/or fails. Email is sent to the 
provided email address. Note replace ``<user@cardiff.ac.uk>`` with your email
address!

My code uses both message passing and thread parallelism. How do I run it?
--------------------------------------------------------------------------
Hybrid programming is possible by specifying the total number of CPUs in the
SLURM directives (MPI tasks multiplied by OpenMP threads). For example::

  #SLURM --nodes=1
  #SLURM --ntasks=8
  #SLURM --ntasks-per-node=8
  #SLURM --cpus-per-task=2

This will reserve one chunk of resource in 1 node with 16 CPUs, the chunk will
have 8 MPI tasks each with 2 (CPUs) OpenMP threads. Another example::

  #SLURM --nodes=2
  #SLURM --ntasks=4
  #SLURM --ntasks-per-node=4
  #SLURM --cpus-per-task=4

This will reserve 2 chunks of resource, 1 in per node, 2 nodes in total, where
each chunk has 16 CPUs and the 16 CPUs are split with 4 MPI tasks and each MPI
task has 4 (CPUs) OpenMP threads.

It can also be important to compile with the thread-safe MPI compiler. To do
this automatically with the Intel MPI libraries use::

  $ mpiifort –openmp hello.f90 –o hello

Where mpiifort will automatically use the thread-safe library due to the
``-openmp`` option.

What limits are imposed on jobs?
--------------------------------
By default there are number of limits to reduce the impact that one user can
have on the system. These are:

.. csv-table:: Partition limits on Hawk
   :file: partition_limits_hawk.csv
   :widths: 20 20 20 20 20
   :header-rows: 1

These limits can be modified if the job requirement exceeds these parameters,
please `contact ARCCA`_ for more details.

My job takes longer than the maximum walltime. How can I run it?
----------------------------------------------------------------
Please `contact ARCCA`_ where we may be able to grant you access to special 
queue limits for your jobs (depending on requirements).

ARCCA recommends running jobs with job walltime limits where possible since
smaller jobs can be run more efficiently by the job scheduler.

Why isn't my job just running?
------------------------------
SLURM attempts to use HAWK as efficiently as possible given the attributes of
jobs and the resources available. If the job is queueing then it may be just
waiting for resources to become free (if possible reduce the walltime limit
requested to allow the job scheduler to fit your job into small gaps within the
queueing system).

Please see the FAQ regarding finding out more details about your job.

My job seems to be running slowly. What should I do?
----------------------------------------------------
First make sure your job is running on the high performance filesystem on
``/scratch``.  The ``/home`` filesystem is provided via NFS which is not
suitable for work.

If you have compiled code yourself then profile your code to see where the
bottlenecks are. This can be done with the ``–pg`` option to the compiler. 
When the software is run a ``gmon.out`` file is created and can be viewed using
gprof.

Occasionally, poor performance can be caused by issues on the compute nodes.

Please `contact ARCCA`_ if you suspect there may be a problem on the cluster or
if you require assistance with profiling your code.

How do I kill a running job?
----------------------------
The SLURM batch manager used on Hawk provides the command::

  scancel <job_identifier>

that allows users to delete their current jobs, where ``<job_identifier>`` is
the job id number assigned to the job when submitted under control of the 
``sbatch`` or ``srun`` commands. 

I can’t kill a job. What should I do?
-------------------------------------
A job that cannot be killed is a very unusual circumstance. First make sure it
is your job you are trying to kill and you are the owner of the job. If there
is no obvious reason why the job cannot be killed please `contact ARCCA`_.

I have a technical problem when running jobs. Who should I contact?
-------------------------------------------------------------------
ARCCA can provide advice to help solve technical problems. We may also raise
the issue with Hawk’s supplier to support the resolution of incidents. Please
do not hesitate to `contact ARCCA`_ should you require any assistance with any
aspect of the service.

..
  LINKS

.. _contact ARCCA:
.. _contact us: arcca-help@cardiff.ac.uk
