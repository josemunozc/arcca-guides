Information Sources
===================

I’m new to HPC. How do I get started? 
-------------------------------------
ARCCA can provide advice and guidance on how your work may benefit from our services,
along with examples of how other researchers across the university and external 
collaborators are making use of Hawk. Please `contact us`_ to discuss your
requirements. 

ARCCA also run a range of training sessions that review *what is supercomputing?* and
also introductory sessions to using the Hawk supercomputer. Please see our 
`Training site`_ for more details. 

How do I use Linux?
-------------------
Once you have logged on to Hawk you will be at what is known as the Linux Shell, or
command line interface. 

ARCCA run a series of introductory training courses, including a tailored 
introduction to Linux – please see our `Training page`_ for more details.

`Contact the ARCCA team`_ for more information and guidance on using Linux.

Where can I find information on using the ARCCA systems?
--------------------------------------------------------
The main local source of information on using the ARCCA systems is the 
`ARCCA Hub site`_.
 
How can I report a problem or raise a query about using the system?
-------------------------------------------------------------------
ARCCA offers a comprehensive and highly-available support network. You can obtain
help by `emailing us`. Emails are automatically directed to the University IT Service
Desk and a call logged on the servicedesk system. You will then receive an email with
a Call Number and the call is forwarded to the ARCCA team for resolution.

Alternatively you can telephone the University IT servicedesk on 
+44 (0) 29 2251 1111.

Does ARCCA run courses on using HPC?
------------------------------------
We offer a wide variety of training courses targeted at multiple levels. Please
visit our `training site`_ for details.

What is the difference between OpenMP and MPI? How can I find out more?
-----------------------------------------------------------------------
OpenMP (Open Multi-Processing) is an API that allows software to take advantage of
multiple processing units in shared memory systems, such as a desktop computer with a
multi-core CPU or a single node on Hawk.

MPI (Message Passing Interface) is a communications protocol that allows the passing
of data between shared memory systems across a network. This allows the splitting up 
of models into discrete components, each communicating with each other periodically
to share data.

As far as Hawk is concerned, OpenMP-enabled software allows you to use only a single
node (albeit multiple cores), whereas MPI allows you to use many nodes at the cost of
complexity and inter-process communication speed.

Here is a `useful MPI vs OpenMP guide`_ if you wish to learn more.

Are there application guides available for commonly used applications?
----------------------------------------------------------------------
Application guides for are available on the `ARCCA Hub site`_ within the 
`ARCCA Hub Training Guides`_ section.

Please `contact us`_ for more information on guides.



..
  LINKS

.. _University IT:
.. _IT Service Desk: it-servicedesk@cardiff.ac.uk
.. _IT Service Desk Portal: https://itservicedesk.cardiff.ac.uk
.. _MySCW: http://my.supercomputing.wales/
.. _ARCCA Team: http://www.cardiff.ac.uk/advanced-research-computing/about-us
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
