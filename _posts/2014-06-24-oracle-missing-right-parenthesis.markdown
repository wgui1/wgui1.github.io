---
layout: post
title: "Oracle --- missing right parenthesis"
date: 2014-06-24 07:15
comments: true
tags: sql
categories: english
---

Met strange error when execute sql in oracle 11g.
    select build_set_status.uuid from build_set_status where build_set_status.project in (select project from tracer_project_1 where tracer_project_1.project like '%tracer' order by project);

After practice googlefu, it turns out the error has been reported since 2008.
And practice is that:
    don't use ORDER BY inside an IN subquery.

Reference:
[ORA-00907: missing right parenthesis](http://oraclequirks.blogspot.com/2008/01/ora-00907-missing-right-parenthesis.html)
[How To Use Order By in Subquery in Oracle](http://blog.agilelogicsolutions.com/2010/11/how-to-use-order-by-in-subquery-in.html)
