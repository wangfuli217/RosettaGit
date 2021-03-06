+++
title = "SystemVerilog"
description = ""
date = 2010-12-05T03:29:25Z
aliases = []
[extra]
id = 8225
[taxonomies]
categories = []
tags = []
+++

{{language|SystemVerilog
|site=http://www.systemverilog.org/
}} is a language used for hardware design and verification. It is defined by IEEE standard 1800-2005, which extends the hardware description language Verilog (IEEE 1364-2001). SystemVerilog has strong support for concurrency, but though the execution model is based on a single thread that provides the illusion of concurrency via a simulation model known as two-list simulation: first all the "outputs" (of all processes) are calculated as functions of the current inputs; and then the inputs to all processes are updated from the outputs that drive them. So, for example:

<lang:SystemVerilog>
  always @(posedge clk) begin
    a <= b;
    b <= a;
  end

```


simply swaps the two values on each rising clock edge. The result of both the the assignments are calculated on their rhs input values at the start of the simulation "delta cycle". Only after both updates are known will the assignments actually be performed. So there is a strong illusion that the two statements execute concurrently.

SystemVerilog adds many features:

Design Subset:

* packed structures and unions
* enumeration types

Verification Subset:

* classes
* (temporal) assertions
* random sequence generation, and constrained random variables
