---
layout: post
title: "So, Scriptella works with Neo4j"
date: 2014-10-27
tags: "gist code sna databases graphs neo4j sql cypher mysql xml scriptella etl java jdbc"
---

We all know that Neo4j's Cypher has recently had a language upgrade to accommodate ETL. Yes, the graph engine now supports `LOAD CSV` within Cypher scripts. 

CSV is a great data interchange format, specially because one can edit, manipulate and filter it with simple command line tools. The only caveat is that it requires a full export of all the data into a text-only format with no widely-accepted standard for reading and writing it. You may run into issues as simple as misdetected text encoding and as complicated as converting string array fields into plain text. Furthermore, `LOAD CSV` covers only the need to import (and not export). 

What if we need to migrate some data back to the good old RDBMS? Isn't there a better, one-shot way for migrating some of our precious graph data into another database? 

Thanks to [Neo4j's JDBC driver](https://github.com/neo4j-contrib/neo4j-jdbc), you can. But then most end-user ETL or data migration applications don't really like a driver that speaks Cypher rather than SQL, and run into all sorts of errors while trying to automatize some aspects of your data access when using Neo4j's JDBC driver. 

One tool that allows you benefit from all the facilities offered by the standardized Java database interfaces and yet perfectly obeys your orders is [Scriptella](http://scriptella.javaforge.com). 

Below is a Scriptella configuration code that shows how to use MySQL and Neo4j JDBC drivers along with Scriptella to run an ETL process. All you need to do is to put the `etl.xml` file in Scriptella's `bin` directory, the JDBC driver files in `lib` directory, and run Scriptella. 

{% gist retrography/1295ba19d0caa73a5dfe %}
