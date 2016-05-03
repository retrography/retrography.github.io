---
layout: post
title: "So, what if you have to migrate from Neo4j to OrientDB?"
date: 2015-04-11
keywords: "neo4j, orientdb, graph, database, etl, import, export, data, graphml"
---

According to [OrientDB's website](http://orientdb.com/docs/last/Import-from-Neo4j-into-OrientDB.html) migrating your data from Neo4j is pretty staightforward, and it involves only three simple steps:

1. Installing [Neo4j shell tools](https://github.com/jexp/neo4j-shell-tools)
2. Exporting your data from Neo4j in GraphML format: `export-graphml -t -o /tmp/out.graphml`
3. Importing your data in OrientDB from GraphML format: `create database plocal:/tmp/db/test` and then `import database /tmp/out.graphml`

In practice there are several limitations that may hinder this supposedly simple process. My recent attempt to transfer some of my data from Neo4j to OrientDB demonstrated at least four:

1. OrientDB won't import nodes that have more than one label associated with them in Neo4j. The solution is to transform all your nodes into single-label nodes before exporting from Neo4j.
2. OrientDB won't import nodes with properties called `id` or `label`. The solution is to rename such properties, if any.
3. OrientDB's console will load the whole GraphML file into Java heap memory before importing it in the database. It will need a maximum heap size at least as large as your GraphML file. The solution is to set the maximum heap size for the console in `$orientdb/bin/console.sh`. In my case this meant adding `JAVA_OPTS="-Xmx8192m"` to line 43 of the script.
4. OrientDB's console is not good with parallel processing. Although database operations are mostly IO-bound, this turns out to be a limiting factor when importing graph data. The solution is to connect to OrientDB remotely rather than natively when using console. To put it in concrete terms, instead of the suggested `create database plocal:/tmp/db/test` you may want to run the following command: `create database remote:localhost/test USERNAME PASSWORD plocal`.  

Once you are done, you can sit back and wait for hours while OrientDB imports the data. The average speed seems to be around 1000 records per second for the edges (8 cores - SSD). The vertices are imported at a much higher rate.
