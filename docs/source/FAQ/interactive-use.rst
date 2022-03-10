Interactive Use
===============

What are the login nodes used for?
----------------------------------
The login nodes are for compiling, debugging, and file editing activities. They
are intended for interactive SSH sessions, file editing, compiling, debugging
and managing jobs in the job scheduler. They are reserved for activities which
do not consume lots of processing or memory resource. Any job dedicated to 
computing must be run on a compute node.

What are Environment Modules?
-----------------------------
ARCCA continually updates application packages, compilers, communications
libraries, tools, and math libraries. To facilitate this task and to provide a
uniform mechanism for accessing different revisions of software, ARCCA uses the
Environment Modules utility.

Environment Modules are predefined environmental settings which can be applied
and removed dynamically. They are usually used to manage different versions of
applications, by modifying shell variables such as PATH and MANPATH.

Modules are controlled through the ``module`` command. Common tasks are shown
here::
 
  module avail	Show available modules
  module load <modulename>	Load a module
  module unload <modulename>	Unload a module
  module swap <modulename>	Swap a loaded module to a different version
  module purge	Unload all modules
  module show	Show the settings that a module will implement
  module help	Display information about the module command
  module help <modulename>	Display information about module <modulename>

Please see the *Quick Start User Guide* for more detailed information.

How do I compile and link my code?
----------------------------------
Compilation and linking is very application-dependent. However, the common
first step should be to load the desired compiler and MPI environment.  Please
see the FAQ describing what compilers are available on Hawk.

For example, for Intel compilers and Intel MPI, use::

  module load compiler/intel
  module load mpi/intel

This will make the compilers available in your path and will set environment
variables such that compiler-dependent and MPI libraries are linked correctly
into your application. (Please remember to load the same modules when it comes
time to run the application via a batch job script.) 

Please note, the Intel compilers generally provide more efficient codes, but
for some open-source software the Intel compilers are not compatible and the
GNU open-source compilers should be used (module load compiler/gnu).

Other libraries that your code uses may also be available via modules. Use
``module avail`` to check, and ``module load <library>`` to load the library
before compiling and linking. A detailed guide to compiling and linking codes
is available in the ARCCA *Quick Start User Guide*. 

Can I use X-Windows applications on ARCCA?
------------------------------------------
X-Windows applications can be run on the Hawk login nodes. To enable your local
machine to act as the X display, log in to Hawk by using::

  ssh –Y <username><at>ravenlogin.arcca.cf.ac.uk

You will of course need to have an X-Windows environment running on your local
machine in order to display the output from the remote application.


