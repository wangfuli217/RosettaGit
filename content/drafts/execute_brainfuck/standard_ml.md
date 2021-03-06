+++
title = "Execute Brainfuck/Standard ML"
description = ""
date = 2010-02-06T14:25:45Z
aliases = []
[extra]
id = 4031
[taxonomies]
categories = []
tags = []
+++

{{implementation|Brainfuck}}{{collection|RCBF}}
Quick implementation of a [[Brainfuck]] interpreter in [[Standard ML]].

Like the [[Haskell]] [[RCBF/Haskell|version]] but without the lazy lists:

Pairs of lists are used to implement both the two-side infinite band of cells, and the program storage.

''run'' interprets a Brainfuck program as a list of characters and reads integers from ''stdin'' and outputs them to ''stdout''.

A more efficient implementation could for example only admit well-bracketed brainfuck programs, and parse bracket blocks first, to replace the ''matchLeft'' and ''matchRight'' which need linear time.


```sml
fun moveLeft  (x::l, r) = (l, x::r)
fun moveRight (l, x::r) = (x::l, r)

fun matchLeft (d as (#"["::_, _)) = d
  | matchLeft (d as (#"]"::_, _)) = matchLeft (moveLeft (matchLeft (moveLeft d)))
  | matchLeft  d                  = matchLeft (moveLeft d)

fun matchRight (d as (_, #"]"::_)) = moveRight d
  | matchRight (d as (_, #"["::_)) = matchRight (matchRight (moveRight d))
  | matchRight  d                  = matchRight (moveRight d)

fun pad ([], []) = ([0], [0])
  | pad ([], r ) = ([0], r  )
  | pad (l , []) = (l  , [0])
  | pad d        = d

fun modify (f, (l, x::r)) = (l, f x :: r)

fun exec (     (_, []     ), _             ) = ()
  | exec (p as (_, #">"::_), d             ) = exec (moveRight p, pad (moveRight d))
  | exec (p as (_, #"<"::_), d             ) = exec (moveRight p, pad (moveLeft  d))
  | exec (p as (_, #"+"::_), d             ) = exec (moveRight p, modify (fn x => x + 1, d))
  | exec (p as (_, #"-"::_), d             ) = exec (moveRight p, modify (fn x => x - 1, d))
  | exec (p as (_, #","::_), d             ) = let val c = valOf (Int.fromString (valOf (TextIO.inputLine TextIO.stdIn))) in
                                                 exec (moveRight p, modify (fn _ => c    , d))
                                               end
  | exec (p as (_, #"."::_), d as (_, x::_)) = (print (Int.toString x ^ "\n");
                                               exec (moveRight p, d))
  | exec (p as (_, #"["::_), d as (_, 0::_)) = exec (matchRight (moveRight p), d)
  | exec (p as (_, #"["::_), d             ) = exec (moveRight p, d)
  | exec (p as (_, #"]"::_), d as (_, 0::_)) = exec (moveRight p, d)
  | exec (p as (_, #"]"::_), d             ) = exec (matchLeft (moveLeft p), d)

fun run s = exec (([], s), ([0], [0]))
```


Example output:


```txt
- run (explode ",[>+<-].>.");
5
0
5
val it = () : unit
```

