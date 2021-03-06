+++
title = "BaCon"
description = ""
date = 2019-07-20T07:52:19Z
aliases = []
[extra]
id = 21311
[taxonomies]
categories = []
tags = []
+++

{{language|BaCon
|site=http://basic-converter.org/
|exec=machine
|gc=yes
|parampass=both
|express=both
|checking=both
|strength=weak
|safety=unsafe
|compat=structural
|hopl=no
|tags=bacon}}
{{implementation|BASIC}}

'''BaCon''', the [[BASIC]] Converter, by Peter van Eerten.

BaCon is a free BASIC to C translator for Unix-based systems, which runs on most Unix/Linux/BSD platforms, including MacOSX. It intends to be a programming aid in creating tools which can be compiled on different platforms (including 64bit environments), while trying to revive the days of the good old BASIC.

BaCon can be described as a translator, a converter, a source-to-source compiler, a transcompiler or a transpiler. It also can be described as a very elaborate preprocessor to C. BaCon is implemented in generic shell script and in itself. Therefore, to start using Bacon, the target system must have either Korn Shell, or ZShell, or Bourne Again Shell (BASH) available. Furthermore, BaCon also works with a newer Kornshell implementation like the MirBSD Korn Shell.

The shell script implementation can convert and compile the BaCon version of BaCon. This will deliver the binary version of BaCon which has an extremely high conversion performance. On newer systems, the average conversion rate usually lies above 10.000 lines per second.

Code converted by BaCon can be compiled by GCC, the Compaq C Compiler, TCC, the clang/LLVM compiler (and possibly by other C compilers), but also by C++ compilers like g++ or clang++.

==See Also==
* http://basic-converter.org/
* http://basic-converter.proboards.com
