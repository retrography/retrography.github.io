---
layout: default
title: data carpentry workshop 2016
---

# data carpentry workshop
## jan. 2016


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

## Cleaning your data with OpenRefine

OpenRefine (Developped by Google as Google Refine and then open-sourced) is a tool for preliminary data cleaning and transformation.

In this section we will use [the open data from Montreal's municipal contracts](http://donnees.ville.montreal.qc.ca/dataset/contrats-octroyes-par-les-fonctionnaires-ville-centrale) to showcase OpenRefine's capabilities. Download the CSV data file from Montreal's open data website.  

Go to [Terminal.com](http://terminal.com) and open the Data Carpentry Workshop's snap. Open Terminal's internal browser on http://localhost:3333. Now upload the data you have downloaded from Montreal Open Data into Open Refine to create a new project.

Now try to:

1. Select `Edit Cells | Transform` and then use the following command to replace all French decimal indicators (commas) with dots: `value.replace(',','.')`.
