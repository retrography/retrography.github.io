---
layout: post
title: "So, one day OrientDB goes to R"
date: 2015-08-05
keywords: "r, orientdb, graphs, databases, statistics, sna, code, driver"
---

Lately, I have been relying on [OrientDB](http://orientdb.com) in order to store my raw data before transferring it to the analysis software like R. OrientDB is the first multi-model database I have ever used, and has turned out to be a great choice as a pre-analysis data storage system. 

Multi-model databases allow the user to save the data using one model (lets say document) and retrieving it using another (e.g. graph). In OrientDB one can query the data as simple tables, or as a document collection, or even as a graph. OrientDB support schemas, but it is pretty relax about them and allows schema-less data just like a document database. It also allows traversing from a document to the other through explicit links, just as a graph database does. But at heart OrientDB is an object-oriented database. It sees everything, any record, edge, vertex or document as a nested or nestable object. Finally, OrientDB supports user-defined functions and complex types such as DateTime. All these make it an extraordinary data gathering tool for the researcher.

![OrientDB](https://upload.wikimedia.org/wikipedia/en/d/dc/OrientdbLogo.png)

What is really lacking in the OrientLand is good interfaces -- and I am excluding its native web-based user interface. Although OrientDB speaks SQL and it should supposedly be easy to access using traditional database interfaces, as of now it only has a half-finished JDBC connector that regularly crashes dbeaver. It doesn't have an equivalent of MongoDB's MongoChef for its document interface either. Importing and exporting standard formats such as CSV and GraphML is a possibility, but depending on the size of data you deal with, can range from being a hassle to becoming impractical. Last but not least, OrientDB still doesn't have a driver in many languages. 

It is this last point that pushed me to write my own R driver, dubbed OrientR, for OrientDB. It happens to me regularly to transfer huge chunks of data from OrientDB to R, and R does not really like the JSON output of OrientDB's REST API. So I decided to develop this lightweight REST API wrapper that can pre-chew OrientDB's output and make it ready for R. The driver can run queries against OrientDB's REST API, clean up the fetched resultset, take care of flattenning the JSON into a dataframe, and also do some automatic or customized type conversion. You can check OrientR out [here](https://github.com/retrography/OrientR). The readme file shows the basic usage and installation, and inside R you can use `?` to look up the more sophisticated options. The objective is to have the driver directly transalte between iGraph and OrientDB some day, but this is just a start. Hope it helps some of you out there get into the multi-model world.
