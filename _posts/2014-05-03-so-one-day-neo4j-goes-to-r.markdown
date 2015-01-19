---
layout: post
title: "So, one day Neo4j goes to R"
date: 2014-05-03
keywords: "r neo4j graphs databases statistics sna code gist"
---
There is an easy way to fetch graph data from Neo4j directly into R environment using a simple REST API client:

{% highlight r linenos %}
library('RCurl')
library('RJSONIO')

query <- function(querystring) {
  h = basicTextGatherer()
  curlPerform(url="http://localhost:7474/db/data/cypher",
    postfields=paste('query',curlEscape(querystring), sep='='),
    writefunction = h$update,
    verbose = FALSE
  )
 
  result <- fromJSON(h$value())
  
  data <- data.frame(t(sapply(result$data, unlist)))
  names(data) <- result$columns
  
  data 
} 
 
# EXAMPLE
# =======
 
# Cypher Query:
>q <- "
match (o:Organization)-[r]-(p:Person) return o.name,o.location,p.account,p.name,p.email limit 20
" 
>data <-query(q)
{% endhighlight %}

***Caution:*** This script runs into trouble if the query response is in a non-tabular format or includes missing values. 

Neo4j does not support null-valued properties and any property with a null value is removed from the database. In other words running `SET node.property = NULL` elicits the same result as running `REMOVE node.property`, which means it deletes the property. Neo4j's REST API responds to queries in JSON, which is schema-less as well, and does not represent missing properties in any way. When converting the JSON output to a tabular format, this results in rows with variable number of columns. 

In case your database contains missing values, either replace them with symbolic values or convert them on the fly within your query. If none of these is an option, you need to use a tabular format like CSV for data interchange.

Credit goes to [Maarten Hermans](https://gist.github.com/mhermans)

