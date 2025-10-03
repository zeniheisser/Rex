# Rex and teaRex

**R**apid **e**vent e**x**traction Version 0.9.9

Rex is a C++ library for parsing and manipulating Les Houches Event-format (LHE) files. It is designed to fast and lightweight, in comparison to internal parsers in programs like MadGraph.
Currently, Rex is in development and may not contain all features necessary for full LHE parsing.

**t**ensorial **e**vent **a**daption with **Rex** Version 0.9.9

teaRex is an extension to the Rex library for the generic reweighting of parton-level events. It provides a flexible framework for applying weight modifications to events based on user-defined criteria, using the underlying Rex formats to sort, extract, and rewrite event-level information, and extending it to allow for generic reweighting using any information stored in an LHE file as input for a user-provided reweighting function acting on REX::process objects, which are SoA (Structure of Arrays) objects for storing event information. Users can either provide the REX::process objects themselves, or use the flexible Rex sorting architecture to extract the necessary information from an LHE file.



Copyright © 2023-2025 CERN, CERN Author Zenny Wettersten.

Licensed under the GNU Lesser General Public License (version 3 or later).

All rights not expressly granted are reserved.


----


## Installation guide

Rex and teaRex are made up of two files each --- an implementation provided in the /src/ directory, and a header provided in the /include/ directory. Any program using Rex needs to include the Rex.h file (i.e. ```#include "Rex.h"```), and at compilation needs to be linked against the compiled library by adding its path to the compile-time ```LDFLAGS```. teaRex is used identically, although note that Rex.h is included in teaRex.h, making it unnecessary to include both (although both compiled libraries still need to be linked against).

A makefile supporting compilation as well as installation (both local and global) are provided with this repository, as the file ```makefile``` in the main directory. Both libraries are compiled with ```-O3``` optimisation by running the ```make``` command here, and can be installed to a specific path by running the commands
```
make
make install PREFIX=/PATH/TO/LIBRARY
```
at which point the headers and compiled shared libraries will be installed at ```/PATH/TO/LIBRARY/include``` and ```/PATH/TO/LIBRARY/lib```, respectively. This command can be used to compile Rex and teaRex system-wide as
```
make
sudo make install PREFIX=/usr/local
sudo ldconfig
```

After installation, compile your program using Rex and teaRex as
```
c++ ... -I /PATH/TO/LIBRARY/include -L /PATH/TO/LIBRARY/lib -lrex -ltearex
```
and your program can now be run as
```
LD_LIBRARY_PATH=/PATH/TO/LIBRARY/lib:$LD_LIBRARY_PATH ./your_binary
```
and your binary should now run using Rex without any issues.