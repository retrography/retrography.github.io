---
layout: post
title: "A simple and effective command-line JSON to CSV convertor"
date: 2015-08-20
keywords: "r csv tabular json hierarchical data conversion wrangling"
---

There are many ways to convert well-structured JSONs into tabular formats like CSV. There is a free tool for that in almost every existing language ([Ruby](https://github.com/korczis/json2csv), [Python](https://github.com/evidens/json2csv), [Go](https://github.com/jehiah/json2csv), etc...). Yet, each time I get my hands on real data the actual conversion process seems elusive. The reason is that most JSON convertors offer way too many options and can quickly become more complicated than a proper procedural conversion.

Most JSON files I need to convert are arrays containing elements (i.e. documents) with similar or identical format. Their elements are not very complex, although sometimes they may contain nested structures. All I expect from a convertor is to (1) detect the schema automatically and (2) flatten the structure, while updating the schema for that. Flattening involves both extracting embedded hashes and converting embedded arrays into strings. What I am particularly wary of is having to create outline files for JSON extraction or having to detect the schema manually in order to name the required fields. 

When I am working in R, I use the excellent [jsonlite](https://cran.r-project.org/web/packages/jsonlite/index.html) package by Jeroen Ooms for such purposes. jsonlite does a good part of the convesion job automatically, but it keeps the embedded lists and vectors (R lingo for array fields) intact. That is why jsonlite's output can't be saved as CSV. jsonlite is quite fast and I trust its JSON parser more than other R/JSON packages. I figured out if I make an executable script out of jsonlite I can use it as my everyday conversion tool...

So, I wrote a tiny script in R that completes the flattening of JSON files by automatically converting array fields into strings. It can read the JSON data from `stdin` or from the file mentioned in command-line arguments. It does not ask for any guidance on what to supress and what to retain. It flattens everything and keeps all the fields in the schema. You will, of course, need R and jsonlite to run it. You can put the script in your `bin` directory and set its execution bit so you can run it like a command (`chmod +x json2csv.R`). It makes a lightway and useful everyday tool.

{% gist retrography/fa622bb57d1ca25ecef8 json2csv.R %}
