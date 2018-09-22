ICE40flow
=========
A simple bash script to drive the ice40 design flow for IceStorm.
Obviously, you need bash and icestorm....

Command Line
============
ice40flow [-n] project

* project is the name of your top Verilog file without the .v extension which is assumed
* -n will stop the workflow from programming the device

Example: ice40flow topmod

This will run yosys, arachne-pnr, icetime, icepack, and iceprog on topmod.v

Configuration
=============
You can control options a few ways.

1. If you want to set global defaults, edit ice40pack and change the DEF_* statements at the top.
2. If you want to set per-directory defaults, put ice40flow.env in the directory and define DEF_* variables there.
3. You can override things on the environment as in: YOSYS_OPTS=-Qq ice40pack top

Things on the command line or the user's environment override things in the .env file and things
in the .env file override things in the global configuration.

Variables
=========
    DEF_YOSYS_LIBDIR = Default library path (colon separated directories; default .:library)
    YOSYS_LIBDIR = The actual library path
    DEF_YOSYS_OPTS = Default yosys command line options (default none)
    YOSYS_OPTS = Actual yosys command line options
    DEF_YOSYS_V_OPTS = Default yosys read_verilog options (default -noautowire)
    YOSYS_V_OPTS = Actual yosys read_verilog options
    DEF_ARACHNE_OPTS = Default arachne-pnr options (default -d 1k)
    ARACHNE_OPTS = Actual arachne-pnr options
    DEF_ICETIME_OPTS = Default icetime options (default -d hx1k)
    ICETIME_OPTS = Actual icetime options
    DEF_YOSYS_PROJECT = Default project name (default none)
    YOSYS_DEFPROJECT = Actual default project
