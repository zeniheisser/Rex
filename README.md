# Rex and teaRex

**R**apid **e**vent e**x**traction Version 0.9.3
Rex is a C++ library for parsing and manipulating Les Houches Event-format (LHE) files.
It is designed to fast and lightweight, in comparison to internal parsers in programs like MadGraph.
Currently, Rex is in development and may not contain all features necessary for full LHE parsing.

**t**ensorial **e**vent **a**daption with **Rex** Version 0.9.3
teaRex is an extension to the Rex library for the generic reweighting of parton-level events.
It provides a flexible framework for applying weight modifications to events based on user-defined criteria,
using the underlying Rex formats to sort, extract, and rewrite event-level information,
and extending it to allow for generic reweighting using any information stored in an LHE file as input for a
user-provided reweighting function acting on REX::process objects, which are SoA (Structure of Arrays)
objects for storing event information. Users can either provide the REX::process objects themselves,
or use the flexible Rex sorting architecture to extract the necessary information from an LHE file.

Copyright © 2023-2025 CERN, CERN Author Zenny Wettersten.
Licensed under the GNU Lesser General Public License (version 3 or later).
All rights not expressly granted are reserved.

