---
title: Understanding HL7 Structure (WIP)
layout: page
date: '2017-03-28 01:00:00'
categories: healthcare
---

# What is HL7
HL7, more formally known as Health Level-7, is a standard used in the healthcare industry to transfer clinical and administrative data. Much like many SaaS services "speak JSON", healthcare applications "speak HL7".

### Versions of HL7
There are two main versions of HL7: **HL7 v2.x** and **HL7 3**.
#### HL7 2.x
HL7 2 was originally created in 1989, dubbed "Pipehat". Since then, we have had a lot of revisions of the standard, giving us:
* HL7 v2.1
* HL7 v2.2
* HL7 v2.3
* HL7 v2.3.1
* HL7 v2.4
* HL7 v2.5
* HL7 v2.5.1
* HL7 v2.6
* HL7 v2.7
* HL7 v2.7.1
* HL7 v2.8
* HL7 v2.8.1
* HL7 v2.8.2

All HL7 2.x versions are **backwards compatible**! This is good news for new HL7 applications, as supporting HL7 v2.7 means that you would be supporting everything from v2.1-v2.7, but not anything above that.

### HL7 v3
HL7 v3 was published in 2005. It is based around a formal methodology called **HDF** (ISO/HL7 27931 for those of you who love standards). It does some really fancy stuff that hasn't really been adopted yet. For this reason, this post will focus mainly on HL7 v2.x.

# HL7 Structure
For this section, we will use the sample HL7 message below (obtained from [here](http://support.pb.com/help/spectrum/9.1/webhelp/en/EnterpriseDataIntegrationGuide/ClientTools/ReadFromHL7/ReadFromHL7.html)) to analyze. Please note that this is dummy data and not actual PII (aka don't sue me, thanks).
```
MSH|^~\&||.|||199908180016||ADT^A04|ADT.1.1698593|P|2.7
PID|1||000395122||LEVERKUHN^ADRIAN^C||19880517180606|M|||6 66TH AVE NE^^WEIMAR^DL^98052||(157)983-3296|||S||12354768|87654321
NK1|1|TALLIS^THOMAS^C|GRANDFATHER|12914 SPEM ST^^ALIUM^IN^98052|(157)883-6176
NK1|2|WEBERN^ANTON|SON|12 STRASSE MUSIK^^VIENNA^AUS^11212|(123)456-7890
IN1|1|PRE2||LIFE PRUDENT BUYER|PO BOX 23523^WELLINGTON^ON^98111|||19601||||||||THOMAS^JAMES^M|F|||||||||||||||||||ZKA535529776
```
To start off, let's look at the image below:
![segments]({{ site.url }}/static/hc/hl7-1.jpg)
  
## The red boxes
Every section inside a red box is called a **segment**. Segments are groups of data that each contain related pieces of information. Each segment has a **carriage return (\r)** at the end of it to demarcate the end of a segment. 

### The green boxes
Each segment begins with a three letter string called a **header**. In this picture, everything in a green box is a header (MSH, PID, NK1, and IN1). Note that the MSH header is special. A segment with an MSH header will *always* begin an HL7 message, and that segment is thus called the **message header**.