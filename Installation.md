# Installation #
## Linux ##

Create a coalition directory.

Download the archive file Coalition-Linux-xxx.0.tar.gz in this directory.

Un-tar it :
tar -xzf Coalition-Linux-xxx.0.tar.gz

Be sure to install pyton 2.5 and twisted matrix (for the server)
Be sure the user used to run the server has the writing permissions in the coalition directory.

To start the server, run 'python server.py' in the coalition directory.

To start the workers, run 'python worker.py' in the coalition directory.

You may have to setup some deamons to do that at the systems startup.

Follow the others instructions on the main page http://code.google.com/p/coalition/

## Windows ##

### For the users ###

A Windows installer is available [here](http://code.google.com/p/coalition/downloads/list). You can install the worker and/or the server. The server is a Windows service and the worker is a command line application. The main
reason for the worker to not be a service is the services can't access the user's network drives.

Once installed, the server service is started and is ready to use.

The installer can register the worker to be started/stopped when the computer go/leave the idle mode. This is done using the Windows task scheduler. It works good under Vista, seams to need some tweeking under XP task scheduler.

### For the developers ###

Install python 2.6, and the corresponding twisted and win32api modules.

  * python : http://www.python.org/download/windows/
  * twisted (for the server) : http://twistedmatrix.com/trac/wiki/Downloads
  * win32api : http://sourceforge.net/project/showfiles.php?group_id=78018

To build the installer :
  * setuptools : http://pypi.python.org/pypi/setuptools
  * zope.interface : http://pypi.python.org/pypi/zope.interface#downloads
  * py2exe
  * NSIS : http://nsis.sourceforge.net/Download
  * NSIS AccessControl plug-in : http://nsis.sourceforge.net/AccessControl_plug-in

# Setup the farm #

The farm should include one server and some workers.

You can first test the server monitor. It should be available through this URL :
http://servername:19211

Once the services are up, the workers will try to connect the server. If all the different computers are on the same local network, the workers should locate the server by themself.

You can see the connected workers in the worker page on the monitor.

The workers should locate the server by themself. If you have multiple servers or if the UDP broadcast doesn't work on your network, you can specify the server url on the command line or in the coalition.ini file, like this :

serverUrl=http://servername:19211

Where "servername" is the name of the server and 19211 its port. 19211 is the default port for a coalition server.

Use the verbose option (-v) on the server and the workers to get more informations on what's going on.