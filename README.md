Interzone Core staging tree 1.5
===============================

http://www.interzone.org

Copyright (c) 2009-2015 Bitcoin Core Developers

Copyright (c) 2014-2015 Dash Core Developers

Copyright (c) 2017-2018 Interzone Core Developers



What is Interzone?
-----------------

Interzone is an experimental new digital token that enables anonymous, instant
transfers to anyone, anywhere in the world. Interzone uses peer-to-peer technology
to operate with no central authority: managing transactions and issuing money
are carried out collectively by the network. Interzone Core is the name of open
source software which enables the use of this token.

For more information, as well as an immediately useable, binary version of
the Interzone Core software, see http://www.interzone.org/


License
-------

Interzone Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see http://opensource.org/licenses/MIT.


Building process
-----------------

**compiling Interzone from git**

Use the autogen script to prepare the build environment.

    ./autogen.sh
    ./configure
    make


Development tips and tricks
---------------------------

**compiling for debugging**

Run configure with the --enable-debug option, then make. Or run configure with
CXXFLAGS="-g -ggdb -O0" or whatever debug flags you need.

**debug.log**

If the code is behaving strangely, take a look in the debug.log file in the data directory;
error and debugging message are written there.

The -debug=... command-line option controls debugging; running with just -debug will turn
on all categories (and give you a very large debug.log file).

The Qt code routes qDebug() output to debug.log under category "qt": run with -debug=qt
to see it.

**testnet and regtest modes**

Run with the -testnet option to run with "play interzones" on the test network, if you
are testing multi-machine code that needs to operate across the internet.

If you are testing something that can run on one machine, run with the -regtest option.
In regression test mode blocks can be created on-demand; see qa/rpc-tests/ for tests
that run in -regtest mode.

**DEBUG_LOCKORDER**

Interzone Core is a multithreaded application, and deadlocks or other multithreading bugs
can be very difficult to track down. Compiling with -DDEBUG_LOCKORDER (configure
CXXFLAGS="-DDEBUG_LOCKORDER -g") inserts run-time checks to keep track of what locks
are held, and adds warning to the debug.log file if inconsistencies are detected.
