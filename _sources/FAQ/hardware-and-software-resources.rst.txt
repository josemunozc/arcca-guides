Hardware and Software resources
===============================

What computer systems are available?
------------------------------------
ARCCA has a variety of available research computing resources, including a
large computing cluster – *Hawk*, a high performance data analytics and AI
platform – *Sparrow*, virtual machine hosting capabilities and a flexible data
storage facility. For more information our services please visit the `ARCCA 
services`_ site. 

What is the difference between Skylake and Rome Nodes?
---------------------------------------------------------------
The Hawk supercomputer system comprises several distinct partitions designed
for different types of jobs. Most of these partitions use Intel Xeon processors
that have an architecture that is code-named *Skylake*, whereas the
``compute_amd`` partition is built from AMD EPYC (*Rome*).

For the user, the main difference is in the number of cores per dual-socket
node, where the *Skylake* partitions have 40 and *Rome* have 64. This means,
for example, that for parallel (MPI) jobs run on the *Rome* partition you
should specify in job scripts, for example::

    #SBATCH --nodes=1
    #SBACTH --ntasks=64
    #SBACTH --ntasks-per-node=64
    #SBATCH --partition=compute_amd

(please not that jobs prepared for ``compute_amd`` must be submitted from the 
``cla1`` login node. You can use ``ssh cla1`` to connect to it.)

and in job scripts to run on most other partitions with *Skylake* nodes::

    #SBATCH --nodes=1
    #SBACTH --ntasks=40
    #SBACTH --ntasks-per-node=40
    #SBATCH --partition=<partition name>

You may also find that some applications are only available on the *Skylake*
systems, and others are only available on *Rome*.

There are a number of differences between *Skylake* and *Rome* architectures
including availability of AVX instructions, cache size and memory bandwidth,
which translates into potentially different application performance. Please
`contact us`_ if your application is not currently available for *Rome*.

How to build a program using MKL?
---------------------------------
Intel’s Math Kernel Library (MKL) is a library of highly optimized, extensively
threaded mathematical routines for applications that require high performance.
If you are using the Intel compilers to build your application, then in most
cases it will be sufficient to use:

``module load compiler/intel``

and include the option ``–mkl`` in your compilation and link commands. (Other
forms which may be useful are ``–mkl=sequential`` to use the non-threaded MKL
and ``–mkl=cluster`` to use libraries like Scalapack built for Intel MPI.)

If your requirements do not fit with the above (e.g. you are using 64-bit
integers or you are using GNU compilers or Open MPI), we recommend that you
visit the `MKL line advisor`_ which provides a tool to generate the required
linker input.

Can I import my own binaries?
-----------------------------
We strongly discourage users from importing their own binaries as these will
not be optimised for our systems. If packages are not available on the HPC
facilities and users require them they should request, where possible, for
ARCCA to install the packages from source on our systems (under the modules
environment). If there is no option but to import a binary it must be compiled
for a 64-bit x86-64 architecture.

What file systems are available?
--------------------------------
There are two main file systems accessible to users on Hawk:
``/home`` contains your home directory. At login, the system automatically sets
the current working directory to your home directory. Store your source code
and build your executables here. This directory can be accessed from any
compute node. Use ``$HOME`` to reference your home directory in scripts. 

``/scratch`` is the directory in which to store large, temporary files.
``/scratch`` is a Lustre file system designed for parallel and high performance
data access from within applications. It has been configured to work well with
MPI-IO, accessing data from many compute nodes. If your jobs have significant
input/output requirements, change to this directory in your batch scripts and
run jobs in this file system.

Please note that neither ``/home`` or ``/scratch`` file systems are backed up.

Users must not use /tmp on each compute node for even the temporary storage of
large data files, as the filling up of this filesystem may cause severe
problems on the service.

Where can I store my research data when it is not being used on the ARCCA systems and is it secure?
---------------------------------------------------------------------------------------------------
Cardiff University provides the `Research Data Store`_ (RDS), a file store service 
specifically for many types of live research data including highly confidential (C1) 
data. 

The `Research Data Store`_ is accessible from Hawk so that data is easily transferred
between the RDS and your ``/home`` and ``/scratch`` directories. Find out how to 
`access the RDS from Hawk`_.

How much does it cost to store my research data?
------------------------------------------------
The `Research Data Store`_ provides a default allocation of 1TB per research project
is available as part of the University's account provision. Allocations above 1TB
and up to 2TB may be provided if certain criteria are met, but these may incur
charges.

How can I check my disk usage?
------------------------------
From your home directory, type ``myquota`` to determine your usage of ``/home``,
``/scratch`` and any shared directories accessible to you.
 
Will my files be backed up?
---------------------------
Backups are not currently provided for data stored on Hawk. We advice users to keep a
copy of any critical data in a suitable external system (e.g. the university 
`Research Data Store`_ or a personal external hard drive).

It is also important to highlight that the ``/scratch`` filesystem is for transient
working data only and may be subject to a 60 day purge policy.

Is there local storage available on each node?
----------------------------------------------
Users must not use ``/tmp`` on each compute node for even the temporary storage of
large data files, as the filling up of this file system may cause severe problems on 
the service.

Use should be made of ``/scratch`` which is designed for parallel and high
performance data access from within applications. ``/scratch`` has been configured to
work well with MPI-IO, accessing data from many compute nodes.

My application requires a large amount of memory. Can it be run on ARCCA?
-------------------------------------------------------------------------
Yes, to an extent. For large-memory jobs, there are a number of options. On the Hawk 
system, submitting to the ``highmem`` partition will allow use of up to 26 hosts each
with 40 cores and 384 GB of memory i.e. 9.6 GByte/core. 

As an alternative, on hosts with 192 GB of memory one could restrict the number of 
running processes so that there is more memory available per process. (This is 
sometimes called *under-committing* or *under-populating* nodes.) For example, to run
12 processes on a 192 GB node, so that each has up to 16 GB of physical memory
available to it, use::

  #SBATCH --nodes=1
  #SBATCH --ntasks=12
  #SBATCH --ntasks-per-node=12
  #SBATCH –-partition=compute

Note that this should only be done if there is a demonstrable need for more than 4.8
GB per process and the alternative ``highmem`` partition is not suitable, as 
under-committing nodes could be viewed as inefficient use of the system.

Is there a list of available applications software?
---------------------------------------------------
The Hawk system has a large number of software packages installed and supported by 
the ARCCA technical staff. See the `Hawk software catalogue`_ for more details.

Why can’t I access some programs?
---------------------------------
Running the command::

  module avail

will return a list of all the modules available to you on Hawk. Please note certain
programs are licensed or available on a restricted basis. If you would like to use a 
program listed there, but cannot gain access, please `contact us`_.

If the program you wish to use is not listed as a module or on the applications page
then again, please `contact us`_.

We are always open to software requests – please see the FAQ regarding software
requests for more information.

Can I request that a new application be installed?
--------------------------------------------------
We are always open to software requests although it may not always be possible to 
install your requested software as it may not be suitable for HPC applications or
maybe cost prohibitive for commercially licensed applications. Please `contact us`_
for more information. Wherever possible we will endeavour to work with customers to
ensure applications or alternatives are suggested.

..
  LINKS

.. _University IT:
.. _IT Service Desk: it-servicedesk@cardiff.ac.uk
.. _IT Service Desk Portal: https://itservicedesk.cardiff.ac.uk
.. _MySCW: http://my.supercomputing.wales/
.. _ARCCA Team: http://www.cardiff.ac.uk/advanced-research-computing/about-us
.. _ARCCA Services: https://www.cardiff.ac.uk/advanced-research-computing/services
.. _email us:
.. _emailing us:
.. _contact ARCCA:
.. _contact the ARCCA team:
.. _contact us: arcca-help@cardiff.ac.uk
.. _Service Status: https://status.cardiff.ac.uk
.. _ARCCA Hub site: https://cf.sharepoint.com/teams/ARCCAHub
.. _ARCCA Hub Training Guides:
    https://cf.sharepoint.com/teams/ARCCAHub/SitePages/ARCCA-Training-Material.aspx
.. _Training site:
.. _Training page:
.. _ARCCA Training site: https://arcca.github.io/
.. _useful MPI vs OpenMP guide:
    http://pawangh.blogspot.co.uk/2014/05/mpi-vs-openmp.html
.. _MKL line advisor:
    https://software.intel.com/en-us/articles/intel-mkl-link-line-advisor/
.. _Research Data Store: 
    https://intranet.cardiff.ac.uk/staff/supporting-your-work/research-support/
    equipment-and-resources/research-data-storage-service
.. _access the RDS from Hawk:
    https://cf.sharepoint.com/teams/ARCCAHub/SitePages/Hawk-Cardiff-Research-
    Datastore-(RDS)-access-VM.aspx
.. _Hawk software catalogue:
    https://cf.sharepoint.com/teams/ARCCAHub/SitePages/Software-Catalogue.aspx
