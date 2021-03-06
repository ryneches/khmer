..
   This file is part of khmer, https://github.com/dib-lab/khmer/, and is
   Copyright (C) 2010-2015 Michigan State University
   Copyright (C) 2015 The Regents of the University of California.
   It is licensed under the three-clause BSD license; see LICENSE.
   Contact: khmer-project@idyll.org
   
   Redistribution and use in source and binary forms, with or without
   modification, are permitted provided that the following conditions are
   met:
   
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
   
    * Redistributions in binary form must reproduce the above
      copyright notice, this list of conditions and the following
      disclaimer in the documentation and/or other materials provided
      with the distribution.
   
    * Neither the name of the Michigan State University nor the names
      of its contributors may be used to endorse or promote products
      derived from this software without specific prior written
      permission.
   
   THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
   "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
   LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
   A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
   HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
   SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
   LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
   DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
   THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
   (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
   OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
   
   Contact: khmer-project@idyll.org

============================
Installing and running khmer
============================

You'll need a 64-bit operating system, internet access, and Python
2.7.x OR Python 3.3 or greater.

Build requirements
------------------

OS X 
^^^^

#) From a terminal download the virtualenv package and create a
   virtual environment with it::

      curl -O https://pypi.python.org/packages/source/v/virtualenv/virtualenv-1.11.6.tar.gz
      tar xzf virtualenv*
      cd virtualenv-*; python2.7 virtualenv.py ../khmerEnv; cd ..
      source khmerEnv/bin/activate

Linux
^^^^^

#) Install the python development environment, virtualenv, pip, gcc, and g++.

   - On recent Debian and Ubuntu this can be done with::

         sudo apt-get install python2.7-dev python-virtualenv python-pip gcc \
                g++

   - For RHEL6::

         sudo yum install -y python-devel python-pip git gcc gcc-c++ make
         sudo pip install virtualenv   

#) Create a virtualenv and activate it::

      cd a/writable/directory/
      python2.7 -m virtualenv khmerEnv
      source khmerEnv/bin/activate

   Linux users without root access can try the OS X instructions above.

Installing khmer inside the virtualenv
--------------------------------------

#) Use pip to download, build, and install khmer and its dependencies::

      pip2 install khmer

#) The scripts are now in the ``env/bin`` directory and ready for your
   use. You can directly use them by name, see :doc:`scripts`.

#) When returning to khmer after installing it you will need to
   reactivate the virtualenv first::

      source khmerEnv/bin/activate

Run the tests
^^^^^^^^^^^^^

After installing you can run the embedded test suite. If you are running an
OSX system you should also add `!linux` to prevent linux-specific tests from
failing.::

      nosetests khmer --attr '!known_failing,!huge'

If the nosetests binary isn't installed then::

      pip2 install khmer[tests]
      nosetests khmer --attr '!known_failing,!huge'
