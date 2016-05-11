---
layout: post
title:  "Apache POI: Handling Excel files with (Java) Play Framework v2.5.x"
date:   2016-05-11 15:20:00 +0530
categories: Java, Play Framework, Excel, POI
---

UNDER CONSTRUCTION
==================

PLEASE TRY AGAIN LATER
======================

The problem: Need to serve arbitrary, on the fly excel files from a Play Framework web app. Excel file must have custom header and footer text along with the actual data.
Things-tried-but-did-not-work-or-worked-partially: Datables (Datatables.net) has options to download tables as .xlsx and it was sufficient for simple use cases. BUT it does not allows any formatting or manuplating data in the excel file. (This was the deal breaker, and is a fine example of when business sense trumps common sense).
Alternative Solutions: Google tells me there arent that many options in the Java world to handle excel files.Dynamic reports (http://www.dynamicreports.org/) seemed promising.


From the top!.
Set up a dummy Play project and run:
> activator new poi-test play-java
> cd poi-test
> sbt run

Add Apache POI to build.sbt (3.14 is the current stable version. check: http://mvnrepository.com/artifact/org.apache.poi/poi/3.14)
libraryDependencies += "org.apache.poi" % "poi" % "3.14"
libraryDependencies += "org.apache.poi" % "poi-ooxml" % "3.14"




<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
