+++
title = "Clojure"
description = ""
date = 2011-09-19T03:00:46Z
aliases = []
[extra]
id = 2901
[taxonomies]
categories = []
tags = []
+++

{{language|Clojure
|site=http://clojure.org/
|exec=bytecode
|gc=yes
|safety=safe
|checking=both
|strength=strong
|LCT=yes}}
{{language programming paradigm|functional}}
{{language programming paradigm|concurrent}}
{{implementation|Lisp}}
Clojure is a dynamic programming language that targets the [[runs on vm::Java Virtual Machine]]. It is designed to be a general-purpose language, combining the approachability and interactive development of a scripting language with an efficient and robust infrastructure for multithreaded programming. Clojure is a compiled language - it compiles directly to JVM [[bytecode]], yet remains completely dynamic. Every feature supported by Clojure is supported at runtime. Clojure provides easy access to the [[Java]] frameworks, with optional type hints and type inference, to ensure that calls to Java can avoid reflection.

Clojure is a dialect of [[Lisp]], and shares with Lisp the code-as-data philosophy and a powerful macro system. Clojure is predominantly a functional programming language, and features a rich set of immutable, persistent data structures. When mutable state is needed, Clojure offers a software transactional memory system and reactive Agent system that ensure clean, correct, multithreaded designs.

==See Also==

* [http://richhickey.github.com/clojure-contrib/ clojure-contrib] -- Clojure's contrib library
