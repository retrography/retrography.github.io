---
layout: post
title: "So, what if all we need is an object's data"
date: 2015-03-23
keywords: "ruby, yaml, hash, json, document, database, convert, data, object, python"
---

Sometimes data comes in objects rather than in well-known hierarchical (e.g. JSON) or tabular (e.g. CSV) formats. It is not always easy to extract the data embedded in objects, specially when the objects contain other nested objects or data structures and do not offer a string representation of their content. While it is possible to implement a serialization method for any object, one may not want to go that far if only the properties need to be extracted out of the object.

Here is a simple solution: Dump the object as YAML, remove the object headers (tags), and then reload the YAML as an object. The reloaded YAML will be a hash containing all the values saved in the properties of the original object. The hash, then, can be converted to JSON or saved in a document database for data analysis. 

The Ruby code follows. Vist the Gist page to see a conversion sample.

{% gist retrography/87b4e25fdecf8307b627 hashject.rb %}

The same method should be applicable to Python objects, except that instead of Ruby's `!ruby/object:` headers, Python's `!python/object/apply:` headers must be removed. 
