Accessing Hawk
==============

Who can access Hawk (the supercomputer)? 
----------------------------------------
Any Cardiff University student, staff, or faculty member may use the system if they 
are a member of a valid registered Hawk project. Valid Hawk projects must have a
Principal Investigator from either Cardiff University or Bangor University. 

Access to external project members (collaborators) can be facilitated via a Cardiff
University staff sponsorship. Cardiff University accounts may be extended for
departing members of staff and students or granted for collaborators from external
institutions in order to facilitate collaboration with Cardiff University
researchers. This usually requires a form to be filled in and signed off by IT Rights
holder for your school (e.g. head of department). We recommend you placing a call
with `IT Service Desk`_ or login to the `IT Service Desk Portal`_ to 
open a ticket for an “Account extension” where they will be able to offer more
specific advice. As soon as the Cardiff University account is extended/granted,
the user account on Hawk can be re-enabled (by contacting us) or requested from the
SCW portal.

How do I apply for access to use the ARCCA systems? 
---------------------------------------------------
Users can register to access Hawk online either by joining an existing project or by 
creating a new one. In order to gain access, users should login to the `MySCW`_
account interface using their institutional user credentials.

On the follow-up details screen, please include a brief statement outlining your 
reason for requesting an account on the system (e.g. 'to apply for a new project for 
abc', 'to join project xyz of PI anon').

Your request will then be seen within our support hours and handled appropriately.
Email notifications will be sent as your request progresses.

Once your account has been approved, access `MySCW`_ again. Your SCW username is now
displayed at the top of the `MySCW`_ page in the Account Summary section. Click
Reset SCW Password and enter a new password for SCW systems. These will be your new
SCW systems username & password and are completely independent of all other
University authentication systems.

*Note:* You need to be a member of a new or existing project to login and run jobs.

Who provides support for ARCCA Systems?
---------------------------------------
Support for the ARCCA facilities is provided by the `ARCCA Team`_. Please 
`contact us`_ if you have any problems, such as requiring the installation of a
package or application or any technical issues.

How do I log in to Hawk?
------------------------
Access to Hawk is via secure shell (SSH, a remote login program), through a login
node which is available from the Internet.  From a Unix system, use:
``ssh <username>@hawklogin.cf.ac.uk``
where ``<username>`` should be replaced by your SCW username provided to you at
registration from within `MySCW`_. 
  
If you are using a Windows computer, you will need an SSH client such as PuTTY to 
access Hawk. PuTTY is available as a networked application on a University imaged PC.

Can I access the Hawk from my personal device?
----------------------------------------------
Hawk can be accessed from anywhere with network connectivity. 

Various clients are freely available and can be installed on tablets and smart
phones. However, these are installed at the users own discretion and ARCCA have no
liability for any software installed on personal devices.   

Further advice on personal device connectivity is provided by `University IT`_.

I can no longer log in to Hawk
------------------------------
Unable to log in to Hawk could be caused by a number of possible reasons:

a. Please first ensure that you are using your SCW username and NOT your University
   username. Your SCW username will have a c. (c dot) prefix.

b. Hawk offline for a maintenance session – Hawk scheduled maintenance occurs as
   required on the first Wednesday of each month. This can be either as a Maintenance
   Outage period or an “At Risk” period. An email will normally be sent to the arcca
   mailing list 2 weeks in advance of a planned outage. The outage will also have 
   been communicated in advance via the Hawk MOTD service. For see the latest updates
   in Cardiff University's Service Status site.

c. Incorrect password – to avoid malicious dictionary-style automated attacks, ARCCA
   have implemented a “five attempt” limit on passwords. If you have typed the
   password incorrectly more than five times (noting it is CASE SENSITIVE), then your
   account will be temporarily suspended for 24 hours. If you need to clear this
   suspension urgently, then please `contact us`_ requesting clearing of incorrect 
   password attempts. *PLEASE NOTE: ARCCA STAFF CANNOT RESET YOUR PASSWORD* (see 
   FAQ’s below regarding password resets).

d. Account expired – if your account has expired then you will require your 
   University sponsor to request reactivation of your UID to University IT. Once this
   is active, you should be able to log on to Hawk with your existing SCW user name 
   and password combination.

e. No Account / Project – prior to being able to access the Hawk supercomputer, you
   need to apply for a user account and project (either added to the membership of an
   existing project, or the creation of a new project on the system). Please see FAQs
   for advice on how to apply for these.

f. Problem on the service – occasionally a component might fail causing a temporary
   service outage. In these instances if the outage is longer than 30 minutes we try
   to inform the user community and provide an estimation of the resolution time (it
   will also form part of the `Service Status`_ page). It can be useful to `contact 
   ARCCA`_ in these instances if you’ve not seen a community announcement, as whilst
   we proactively monitor for alerts it is on a best endeavours basis outside of 
   standard working hours.

How do I configure my PuTTy client to not time out due to inactivity?
---------------------------------------------------------------------

The ssh client PuTTY can be configured to maintain a connection and not time out 
due to inactivity.

To set up a new connection with "keep alives" to maintain your connection follow 
the steps below:

1. Open the PuTTy application and navigate to the Options panel.
2. Select Connection
3. In the field Sending null packets to keep session active change the default 
   value from 0 to 1800 (30 minutes)
4. Check the Enable TCP keepalives (SO_KEEPALIVE option) check box.
   Note: This option may not be available in older versions of the PuTTY client.
5. Select Session from the left hand menu.
6. In the Host Name (or IP Address) field enter the destination hostname, for 
   example vayu.nci.org.au
7. In the Saved Sessions box enter a name for the session, for example keepalive.
8. Select Save

Any new sessions will now use these modified connection options.

Note that to avoid excess logins, Hawk will automatically disconnect sessions that 
have been inactive for more than 2 hours.

How do I change my password?
----------------------------
You can reset your SCW password at the command-line using the Linux ``passwd`` 
command. Alternatively, you may use the `MySCW`_ interface to do this.

I’ve forgotten my password. What should I do?
---------------------------------------------
You can reset your SCW password in `MySCW`_.

How do I add new users to my project?
-------------------------------------
Users can apply to join a project within `MySCW`_ but will need to ask the Technical
Lead of the project to provide the project code. Project codes follow the format 
*scwXXXX* where XXXX are all numbers. The Technical Lead can find their project codes
on the Project Memberships page where they will be listed as Project Owner. Users 
can apply to join via the Join a Project item on the Dashboard. Technical Leads will 
be notified and then need to approve the request.

How do I transfer files to and from Hawk?
-----------------------------------------
From a Unix system, the ``scp`` command can be used to transfer files to and from a 
Hawk login node. For example:

``scp <file> <username>@hawklogin.cf.ac.uk:``
*(Note the colon terminating the remote system name.)*

For Windows-based users, a file transfer utility will need to be installed e.g., 
FileZilla or Winscp.

Are there quotas on CPU and disk usage?
---------------------------------------
Strict quotas are not applied on CPU usage, although Users are expected to comply 
with any fair usage policies which require that no user should have more than 20 jobs
in the scheduler at any one time.

There is a 50 GB limit quota on /home storage – users requesting an increased
allocation should `contact ARCCA`_.

Regular clean-up of ``/scratch`` storage will be introduced shortly following an 
email communication to the user community. 

I need to finish my project urgently. Can I get priority access to the computers?
---------------------------------------------------------------------------------
We are always sympathetic to the requirement for priority access, but need to balance
such requests against the requirements of the user community as a whole. Please 
`contact us`_ specifying your requirement and we’ll respond without delay.



..
  LINKS

.. _University IT:
.. _IT Service Desk: it-servicedesk@cardiff.ac.uk
.. _IT Service Desk Portal: https://itservicedesk.cardiff.ac.uk
.. _MySCW: http://my.supercomputing.wales/
.. _ARCCA Team: http://www.cardiff.ac.uk/advanced-research-computing/about-us
.. _contact ARCCA:
.. _contact us: arcca-help@cardiff.ac.uk
.. _Service Status: https://status.cardiff.ac.uk
