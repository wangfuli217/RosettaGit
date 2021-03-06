+++
title = "SMEQL"
description = ""
date = 2011-12-12T03:01:15Z
aliases = []
[extra]
id = 3202
[taxonomies]
categories = []
tags = []
+++

{{language|SMEQL
|site=http://www.c2.com/cgi/wiki?TqlRoadmap
|LCT=no
}}

SMEQL is a draft query language that is meant to solve the shortcomings and annoyances of [[SQL]]. SMEQL stands for "structured meta-enabled query language" (pronounced "smeegle").

It is influenced by IBM's "Business-System 12" (BS-12) relational query language. BS-12 predated SQL, but was rejected over SQL because IBM felt it was too "mathy", potentially harming sales. However, it's math-like nature is also what makes it more powerful than SQL. It's designed to please nerds, not managers. (It uses "functional programming" to be more specific.)

The general syntax of an element is:

  resultTable = operation(parameters.....)

One can optionally nest these:

  t1 = foo(blah)
  t2 = bar(t1, zog)

to get this:

  t2 = bar(foo(blah), zog)

The final result set name is not needed. Thus, one could type:

  bar(foo(blah), zog)

However, examples here will not use the nested form. The intermediate tables should be considered virtual tables. They are not assumed to be "saved" unless explicitly requested by other operations. They are merely a way to linguistically reference query "chunks". (SQL provides views and/or nested SELECT's for a similar purpose, but these are often awkward or require DBA's.)

Here is a sample to whet your appitite:

  srt = orderBy(Employees, [dept, salary], order)
  top = group(srt, [(dept) dept2, max(order) order])
  join(srt, top, a.dept=b.dept2 and b.order - a.order < 6)

This example returns the top 6 earners in each department based on
this table schema:

  table: Employees
  ----------------
  empID
  dept
  empName
  salary

Here's a brief summary of common SMEQL operators:

* '''calc'''(table, columnTable)  // ''similar to SELECT clause in SQL''
* '''filter'''(table, expression)  // ''similar to WHERE clause in SQL''
* '''group'''(table, columnTable)  // ''roughly similar to GROUP BY in SQL''
* '''join'''(table_1, table_2, expression)
* '''leftJoin'''(table_1, table_2, expression)
* '''orderBy'''(table, columnTable, [sequenceColumn]) // ''sorts or produces sequence numbers''
* '''union'''(table_1, table_2)

A "column table" is merely a way to represent or store column information in tabular form. SMEQL provides a shortcut syntax that is similar to an SQL "WHERE" clause. Any place above where a column-table is required, one can use the shortcut syntax within square brackets "[...]" (not to be confused with "optional" syntax indicators). Column tables potentially allow you to "calculate" column lists instead of having to type them in manually.

More info can be found at: http://www.c2.com/cgi/wiki?TqlRoadmap
