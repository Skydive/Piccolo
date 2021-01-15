The feature-ndmreset branch:
This incorporates some changes to the reset arrangements.
o  There is a "completion of bitstream loading" Reset (aka power-on reset
"por"), which is used to reset the debug module.
o  P1_Core exports a Reset ndm_reset, stimulated by the ndm reset client of
the debug module, and asserted for a parameterizable number of cycles.  (It is
expected that this will be used to reset all or most of the surrounding SoC.)
o  A little consequential plumbing.

>================================================================
Copyright (c) 2019 Bluespec, Inc.  All Rights Reserved.

This directory is intended for DARPA SSITH users; others may safely ignore it.

This directory contains a wrapper and other resources that package up
Piccolo to fit into the "standard" core socket in the SSITH GFE
("Government Furnished Equipment").

>================================================================
Context:

The SSITH system is an SoC with a "socket" (placeholder) for a "Core"
module (a RISC-V CPU).  Various implementations are/will be plugged
into this socket:

 - "P1"
    - Baseline Piccolo (BSV) based core
    - Baseline Rocket (Chisel) based core
    - Variations/alternatives by various SSITH project teams

 - "P2"
    - Baseline Flute (BSV) based core
    - Baseline Rocket (Chisel) based core
    - Variations/alternatives by various SSITH project teams

 - "P3"
    - Baseline Bassoon (BSV) based core
    - Baseline BOOM (Chisel) based core
    - Variations/alternatives by various SSITH project teams

>================================================================
Whenever there are changes to the Piccolo core, rerun:

  $ make compile
      (which generates RTL and then $ cp Verilog_RTL/* xilinx_ip/hdl/)

>================================================================
