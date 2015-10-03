---
layout: page
title: resources
---

A list of resources and tools that I find useful, for me and for every researcher...

## Data Wrangling & Analysis

### Languages & Coding Environments

* [Shell Scripting](http://www.freeos.com/guides/lsst/)
	* [coreutils](http://www.gnu.org/software/coreutils/coreutils.html) -- Perfect set of data tools for the Penguin-hearted: `cat`, `tac`, `cut`, `paste`, `head`, `tail`, `tr`, `wc`, `sort`, `shuffle`, `uniq`, `expr`, `join`, `fold`, `expand`, `tee`, `mkfifo`
	* [moreutils](http://joeyh.name/code/moreutils/) -- Some additions to the `coreutils`: `sponge`, `parallel`
	* [grep/egrep](http://www.grymoire.com/Unix/Grep.html) -- Text matching using Regular Expressions
	* [sed](http://www.grymoire.com/Unix/Sed.html) -- Text replacement using Regular Expressions
	
* Regular Expressions
	* [The Bible](http://www.regular-expressions.info)
	* [regexplanet](http://www.regexplanet.com) -- testing for all regex flavors
	* [regxr](http://www.regexr.com) -- testing
	
* [Ruby](https://www.ruby-lang.org/en/) -- The pretty
	* [Interactive Course](http://tryruby.org)
	* [Mr. Neighborly's Humble Little Ruby Book](http://humblelittlerubybook.com/book/html/index.html)
	* [Ruby Essentials](http://www.techotopia.com/index.php/Ruby_Essentials)

* [R](https://www.r-project.org) -- The nasty
	* [Fast Intro](http://data.princeton.edu/R)
	* [DataCamp R Courses](https://www.datacamp.com)
	* Books
		* [R Cookbook](http://www.cookbook-r.com) -- Introductory book
		* [The Art of R Programming](http://heather.cs.ucdavis.edu/~matloff/132/NSPpart.pdf) -- Introduction and beyond
		* [The Bible](http://adv-r.had.co.nz) -- by Hadley Wickham
	* [R Reference Card 2.0](https://cran.r-project.org/doc/contrib/Baggott-refcard-v2.pdf) -- R in 6 pages
	
	* [RStudio](https://www.rstudio.com) -- The IDE
	* [Revolution R](https://mran.revolutionanalytics.com/download/) -- The better, faster R
	* Packages
		* [dplyr Package]() -- Data Frame manipulation made easy ([Intro](https://cran.rstudio.com/web/packages/dplyr/vignettes/introduction.html) | [Course](https://www.datacamp.com/courses/dplyr-data-manipulation-r-tutorial) | [Cheat Sheet](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf) | [On plyr](http://seananderson.ca/2013/12/01/plyr.html))
		* [tidyr Package](https://cran.r-project.org/web/packages/tidyr/index.html) -- Unmess your data ([Vignette](https://cran.r-project.org/web/packages/tidyr/vignettes/tidy-data.html) | [Cheat Sheet](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf))
		* [reshape2 Package](https://cran.r-project.org/web/packages/reshape2/index.html) -- From wide to long data and vice versa ([Intro](http://seananderson.ca/2013/10/19/reshape.html))
		* [magrittr Package](https://cran.r-project.org/web/packages/magrittr/index.html) -- Linux pipes for R ([Vignette](https://cran.r-project.org/web/packages/magrittr/vignettes/magrittr.html) | [dplyr and pipes](http://seananderson.ca/2014/09/13/dplyr-intro.html))
		* [jsonlite Package](https://cran.r-project.org/web/packages/jsonlite/index.html) -- From JSON to Data Frame
		* [lubridate Package](https://cran.r-project.org/web/packages/lubridate/index.html) -- Date/Time lubricated and on steroids ([Vignette](https://cran.r-project.org/web/packages/lubridate/vignettes/lubridate.html))
		* [stringr Package](https://cran.r-project.org/web/packages/stringr/index.html) -- Strings for mere mortals ([Vignette](https://cran.r-project.org/web/packages/stringr/vignettes/stringr.html))
		* [data.table Package](https://cran.r-project.org/web/packages/data.table/index.html) -- ([Intro](https://cran.r-project.org/web/packages/data.table/vignettes/datatable-intro.pdf) | Vignettes: [Basics](https://cran.r-project.org/web/packages/data.table/vignettes/datatable-intro-vignette.html), [Keys & Search](https://cran.r-project.org/web/packages/data.table/vignettes/datatable-keys-fast-subset.html), [Referencing](https://cran.r-project.org/web/packages/data.table/vignettes/datatable-reference-semantics.html), [Reshaping](https://cran.r-project.org/web/packages/data.table/vignettes/datatable-reshape.html) | [Cheat Sheet](https://s3.amazonaws.com/assets.datacamp.com/img/blog/data+table+cheat+sheet.pdf)) -- The most usable data frame extension

* [Python](https://www.python.org) -- The serious

* [Julia](http://julialang.org) -- The junior
	* [juliabox](https://www.juliabox.org) -- Julia testdrive

* [Pig](https://pig.apache.org) -- Playing it big
	* [Learn Pig](http://help.mortardata.com/technologies/pig/learn_pig)
	* [Pig Cheatsheet](http://mortar-public-site-content.s3-website-us-east-1.amazonaws.com/Mortar-Pig-Cheat-Sheet.pdf)

* [Gremlin](http://tinkerpop.incubator.apache.org) -- The graph language
	* [Gremlin Docs](http://gremlindocs.com/)
	* [Gremlin Tutorial](https://github.com/tinkerpop/gremlin/wiki)

### Graphs & Network Analysis

* [iGraph](http://igraph.org) -- Fast and furious 
* [Statnet](https://statnet.org) -- The classic
* [SNAP](http://snap.stanford.edu) -- Up & coming
* [RSiena](http://www.stats.ox.ac.uk/~snijders/siena/) -- Longitudinal networks
* [NodeXL](https://nodexl.codeplex.com) -- A first try
* [Pajek](http://vlado.fmf.uni-lj.si/pub/networks/Pajek/) -- Old McDonald had a farm
* [GraphX](https://spark.apache.org/graphx/) -- Playing it big
* [NetworkX](https://networkx.github.io) -- If you need time to sleep
* [graph-tool](http://graph-tool.skewed.de) -- Up & coming

### Graph Databases

* [OrientDB](http://orientdb.com) -- A database for all seasons
* [Neo4j](http://neo4j.com) -- The beauty
* [Titan](http://thinkaurelius.github.io/titan/) -- Playing it big
* [ArrangoDB](http://www.arangodb.com) -- Up & Coming

## Basics

### Shells & Terminals

* [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) -- Very nice set of shell configurations. Use with [agnoster](https://gist.github.com/agnoster/3712874).
* [iTerm2](https://www.iterm2.com/) -- The ultimate terminal
* [TotalTerminal](http://totalterminal.binaryage.com) -- Quake-style HUD console for OSX

### Versioning, Repos, Dependency Management

* [Homebrew](http://brew.sh) -- OSX's missing package manager. You need this to install most of the tools mentioned here.
* [Homebrew Cask](http://caskroom.io) -- Automated software installer for OSX

* [Git](http://www.git-scm.com) -- Linus Torvald's choice of versioning system
	* [Step by Step for the Beginner](https://blog.udemy.com/git-tutorial-a-comprehensive-guide)
	* [Fast Intro](https://www.atlassian.com/git/tutorials/setting-up-a-repository)
	* [Interactive Course](https://try.github.io)
	* [Bible](http://www.git-scm.com/book/en/v2)

### Backup

* [S3/Glacier](http://aws.amazon.com/s3/) -- Cheap storage
* [s3cmd](http://s3tools.org/s3cmd) -- S3 client toolset
* [Duplicity](http://duplicity.nongnu.org) -- The quintessential incremental backup software
* [rsync](https://rsync.samba.org) -- Royal sync
* [Globus](https://www.globus.org) -- Fast and secure data transfer for academics

### Compute

* [Compute Canada](https://www.computecanada.ca) -- Maple Leaf computing force
* [Calcul Quebec](http://www.calculquebec.ca/en/) -- Je me souviens computing force
* [McGill HPC](http://www.hpc.mcgill.ca) -- Martlet computing force
* [terminal.com](https://www.terminal.com) -- Pausible virtual machines
* [DigitalOcean](https://www.digitalocean.com) -- All-SSD cloud

### Editors

* [Vim](http://www.vim.org/) -- The classic
* [Textmate](http://macromates.com) -- The pro choice
* [Atom](https://atom.io) -- The chameleon/editor


