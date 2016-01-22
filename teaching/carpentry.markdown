---
layout: default
title: data carpentry workshop 2016
---

# data carpentry workshop
## jan. 22, 2016


## Terminal.com, research scientist's best friend

[Terminal.com](http://terminal.com) offers you a range of affordable and easily scalable virtual machines where you can install your required software without manipulating your personal computer. Most of the freely distributable software are already available on Terminal as duplicable images. Simply find your image, and launch it. You can adjust the specifications of your machine while working. The machine will pause automatically if you stop working with it.

Head over to [Terminal.com](http://terminal.com) and create a free account. You may need to spend a few bucks to charge your account so that you can keep your virtual machine running during the workshop.

Now that you have an account, launch a new terminal based on [this snap](https://www.terminal.com/tiny/ArQMhWMBlM). We will use this terminal for several exercises.

## Scraping data from the web using KimonoLabs

[Ryan Rowe and Pratap Ranade](http://www.wired.com/2014/03/kimono/) have suffered their way through PhD programs in their earlier lives, so when they decided to design a data gathering interface, they knew they didn't want their clients to suffer. [KimonoLabs](https://www.kimonolabs.com) has been up for less than two years now, and with its intuitive and smart interface it has brought web scraping to a new level. Open a free KimonoLabs account and download [the Kimono extension](https://chrome.google.com/webstore/detail/kimono/deoaddaobnieaecelinfdllcgdehimih) for Google Chrome as well. You will also need the [Kimono add-on](https://chrome.google.com/webstore/detail/kimono/gincecdpheaeldbkjinnmloiiomnakee) for [Google Sheets](https://docs.google.com/spreadsheets). Open a Google Sheet and install the Kimono add-on from the add-ons menu.

In this section we will:

1. Scrape the first two pages of [McGill Events page](http://mcgill.ca/channels/events) (Event titles, sources and times/dates)
2. Use the obtained data to scrape the content of individual McGill event pages
3. Import the scraped data into a Google Sheet

## Importing different data formats

There are different data import functions embedded in Google Sheets. I have prepared [a special Google Sheet loaded with additional data import functions](https://drive.google.com/open?id=1rRev0tKulMWhOS7mepJm65u27Kdr-VqOi_xYHwjHAl4). Make a copy of this Google Sheet in your own Google Drive. Now use this spreadsheet to do the following:

1. Import the CSV file from [Montreal Resident Satisfaction Survey](http://donnees.ville.montreal.qc.ca/dataset/sondage-satisfaction-citoyens) using [IMPORTDATA](https://support.google.com/docs/answer/3093335) function.
2. Import the XML file listing [Montreal's skating rinks](http://donnees.ville.montreal.qc.ca/dataset/patinoires) using [IMPORTXML](https://support.google.com/docs/answer/3093342) function.
3. Import the JSON file containing [Montreal's public art work inventory](http://donnees.ville.montreal.qc.ca/dataset/art-public-information-sur-les-oeuvres-de-la-collection-municipale) in Google Sheets using [ImportJSON](http://blog.fastfedora.com/projects/import-json) function.

Today most data feeds come in hierarchical formats. On the other hand, analysis tools accept only tabular formats. This makes the tabular <=> hierarchical conversion a necessity. There are better, more sophisticated tools for converting hierarchical formats to tabular formats. Two examples are `xmllint` and `jq`, both installed on your Terminal virtual machine.

## Cleaning your data with OpenRefine

OpenRefine (Developped by Google as Google Refine and then open-sourced) is a tool for preliminary data cleaning and transformation.

In this section we will use [the open data from Montreal's municipal contracts](http://donnees.ville.montreal.qc.ca/dataset/contrats-octroyes-par-les-fonctionnaires-ville-centrale) to showcase OpenRefine's capabilities. Download the CSV data file from Montreal's open data website.  

Go to [Terminal.com](http://terminal.com) and open the Data Carpentry Workshop's snap. Open Terminal's internal browser on http://localhost:3333. Now upload the data you have downloaded from Montreal Open Data into Open Refine to create a new project.

Now try to:

1. Select `Edit Cells | Transform` from the column "MONTANT"'s contextual menu and then use the following command to replace all French decimal indicators (commas) with dots: `value.replace(',','.')`.
2. Now use `Edit Cells | Common Transforms | To number` on the same column to convert the values to number.
3. Now define a facet (Facet | Numeric Facet) on the column. What is the range of the contracts? Select the most expensive contracts (above 5 millions) and sort them numerically.
4. Now use `Edit Cells | Cluster and edit...` on the "APPROBATEUR" field to cluster the alternative spellings.
5. Use the method "key collision" with function "fingerprint" the first time. Correct all the misspelling.
6. Now use the method "nearest neighborhood" with function "levenshtein". Isn't this cool?

## Linux command line: The holy grail

All the automated tools have their limitations that prevents you from having close access to your data. In many cases the only tools that work are the simplest ones, the bare-bone command line tools. Linux's GNU tools are very rich in this sense. They provide you with all you need for data preparation, specially when very large files are involved.

### Your first commands

- Download the list of all public trees in downtown Montreal using the following command:

```
wget http://donnees.ville.montreal.qc.ca/dataset/3e3efad6-9f2f-4cc0-8f1b-92de1ccdb282/resource/7873dfd4-ff95-40e0-af3a-3c35f784a927/download/villemariearbrespublics20151202.zip
```

In order to decompress the file:

```
tar xvf villemariearbrespublics20151202.zip
```

One of the amazing capabilities of Linux is piping. Using pipes you can take the output from one command and send it to another command. We indicate a pipe with the `|` (pipe) character. Let's do the above exercise with pipes:

```
curl http://donnees.ville.montreal.qc.ca/dataset/3e3efad6-9f2f-4cc0-8f1b-92de1ccdb282/resource/7873dfd4-ff95-40e0-af3a-3c35f784a927/download/villemariearbrespublics20151202.zip | tar xv
```

Like this you will never see the zip file. The zip file will be handed over to the unzip utility on the fly and as a stream. The unzipped version of the file will be written to the disk subsequently.

The pipes are very useful for data processing, and we will spend some time on them. Now let's have a look at this whopping 30MB text file.

Lets first rename the file:

```
mv Ville_Marie_Arbres_publics_2015_12_02.csv trees.csv`
```

To see the first ten lines of the file:

```
head trees.csv

# or

head -n 10 trees.csv
```

To see the last ten lines of the file:

```
tail trees.csv

# or

tail -n 10 trees.csv
```

`tail` command has another interesting use. It can suppress the first lines of a file and output the rest. The following command starts displaying a file from the second line:

```
tail -n +2 trees.csv

# and of course you can pipe

head -n 5 trees.csv | tail -n +2 trees.csv
```

Linux also has a command called `cat` that can display the entirety of a file. You don't really want to try that on such a large file, but maybe you can use it in combination with a pagination software to limit the output:

```
cat trees.csv | less
```

The file seems to be a semicolon-delimited text file. But there seems to be something wrong with it. It looks like a legacy Windows file with the old encoding. Let's first recode it to the modern unicode.

```
iconv -f WINDOWS-1252 -t UTF-8 trees.csv > out.csv
```

Here the `>` (greater than) sign tells the command to save its input inside a file called `out.csv`. This is another useful feature of Linux command line. You can define inputs and outputs for most commands using `<` and `>`. These are called, by order of appearance, standard input (stdin) and standard output (stdout).

Now that you have the file in UTF-8 format have a look at it. Now the characters look good.

Another set of very useful Linux commands are `cut` and `paste` These two work with character-delimited files as if they are database files!

get the ones from plateau (and convert on the fly)
join them with these ones

```
curl http://donnees.ville.montreal.qc.ca/dataset/3e3efad6-9f2f-4cc0-8f1b-92de1ccdb282/resource/0cd2ff7a-039a-40ac-8844-ce6465cac2a2/download/leplateaumontroyalarbrespublics20151202.zip | tar xv
iconv -f WINDOWS-1252 -t UTF-8 Le_Plateau_Mont_Royal_Arbres_publics_2015_12_02.csv> out2.csv
tail -n +2 out2.csv > out3.csv
cat out.csv out3.csv > alltrees.csv
```

now you have a 80mb file!

now let's try to extract some information

let's see if we have downloaded the right files and there are only trees from downtown and pleateau in the file.

In order to do this, we need to extract one column of the file. That would eb the 3rd column. (see with `head` command).

Now we use `cut` to get out that specific column. But we only need the distinct values, so we pipe the results into a command aptly called `uniq`.

```
cut -d ';' -f 3 alltrees.csv | uniq
```

> Note: You must always use the command `sort` on the data you are passing into `uniq`, unless you now for sure that your data is sorted.
