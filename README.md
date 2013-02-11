# IPython Notebook Workshop

Below is a compilation of installation instructions and links to various materials that will be useful to anyone using IPython Notebook as a research notebook.


## Installing IPython Notebook on Windows

Windows users have two options for installing IPython Notebook. <a href="https://github.com/JorySchossau">Jory Schossau</a> has put together <a href="https://github.com/JorySchossau/ipynbez#install-and-use">a single executable</a> that installs everything you need for the latest version of IPython Notebook. Alternatively, follow the instructions below to install IPython Notebook with the Enthought Python Distribution.

### Enthought Python Distribution

Download the free version of the Enthought Python Distribution (EPD): http://www.enthought.com/products/epd_free.php

Install EPD into the default directory it suggests.

You now have IPython and most of the libraries you need installed. However, they're mostly older versions, so let's update them real quick.

### Update IPython

Let's get the latest version of IPython so we have the latest and greatest features. Enter the following commands into the Command Prompt, one at a time.

	enpkg enstaller
	enpkg ipython
	
If it asks you you want to run the executable, click Yes.

### pandas library

pandas isn't required for IPython Notebook, but it's the best library in Python for handling data.

Enter the following command into the Command Prompt:

	enpkg pandas
	
If it asks you you want to run the executable, click Yes.

### Run IPython Notebook

Now you should be ready to enjoy IPython Notebook! Enter the following command in the Command Prompt to fire it up:

	ipython notebook --pylab=inline



## Installing IPython Notebook on Mac and Linux

### Enthought Python Distribution

Download the free version of the Enthought Python Distribution (EPD): http://www.enthought.com/products/epd_free.php

Install EPD into the default directory it suggests.

### Update IPython

You now have IPython and most of the libraries you need installed. However, they're mostly older versions, so let's update them real quick.

Enter the following commands into the Terminal, one at a time. If may ask for your password for the `sudo` command.

	sudo enpkg enstaller
	sudo enpkg ipython
	
### pandas library

pandas isn't required for IPython Notebook, but it's the best library in Python for handling data.

Enter the following command into the Command Prompt:

	sudo enpkg pandas

### Run IPython Notebook

Now you should be ready to enjoy IPython Notebook! Enter the following command in the Terminal to fire it up:

	ipython notebook --pylab=inline

<br /><br />

# IPython Notebook tips & tricks

Here are a handful of tips and tricks that I've come across that are helpful for working with IPython Notebook.

## Automatic backup with Dropbox

Backing up your notebooks is crucial to never losing your research notes. Set up a folder in your Dropbox directory (called, say, "notebooks") and always run IPython Notebook from there. Whenever you save the changes you made to a notebook, those changes are automatically backed up on Dropbox.

## Mac/Linux users: set up an alias for IPython Notebook

Instead of having to change to the right directory then remembering the proper command to start up IPython Notebook, just make an alias! Edit your ~/.profile and add the following:

	# change ~/Dropbox/notebooks/ to whatever directory you are storing your notebooks in. I recommend a Dropbox directory!
	alias ipn="cd ~/Dropbox/notebooks/; ipython notebook --pylab=inline"
	
Now you can just type `ipn` into your command line anywhere, and you'll load IPython Notebook right up!

<br /><br />

# Learn to mark up text with MarkDown

John Gruber put together a <a href="http://daringfireball.net/projects/markdown/syntax">concise tutorial</a> explaining how all of the MarkDown language works. I recommend referring to that tutorial whenever you want to figure out how to do something in MarkDown.

<br /><br />

# Learn to code in Python

If you want to learn how to code in Python, Drs. Bill Punch and Richard Enbody have put together a series of <a href="http://www.cse.msu.edu/~cse231/Videos/">video tutorials</a> covering the core features of the Python language.

<br /><br />

# Practice statistical analysis

As a part of this workshop, we're going to do a little statistical analysis on some data to get a feel for what IPython Notebook can do.

## Example data file

I have included a data file with this tutorial titled `parasite_data.csv`, courtesy of <a href="http://luiszaman.com/">Luis Zaman</a>. Please note that this is unpublished data, and is **only meant to be used for the purposes of this workshop**. Email Luis directly if you want to use it for something else.

The data file has 3 columns:

* Virulence

* Replicate

* ShannonDiversity

For our purposes, all we care is that the first two columns (`Virulence` and `Replicate`) are the experimental predictors, and the third column (`ShannonDiversity`) is the measured response from the experiment. Thus, we are interested in what effects `Virulence` and/or `Replicate` have on the measured `ShannonDiversity`. Talk to Luis if you want to know more about the data.

What interesting statistical analyses could we do with these data?

## Reading data

Remember when I had you install the `pandas` library? Here's why: it makes reading data files like this ridiculously easy!

	from pandas import *
	
	# read data from data file into a pandas DataFrame  
	parasiteData = read_csv("parasite_data.csv", # name of the data file
					sep=",", # what character separates each column?
					na_values=["", " "]) # what values should be considered "blank" values?

And there you have it! It reads in the entire file, and you can do all kinds of neat stuff with the data.

	# display the values for the "Virulence" column
	print parasiteData["Virulence"]
	
	# display the values for the "ShannonDiversity" column where "Virulence" == 0.5
	print parasiteData[parasiteData["Virulence"] == 0.5]["ShannonDiversity"]
	
	# display the mean "ShannonDiversity" for the experiments where "Virulence" == 0.7
	print parasiteData[parasiteData["Virulence"] == 0.7]["ShannonDiversity"].mean()
	
pandas DataFrames have all kinds of methods built in, including a bunch of <a href="http://pandas.pydata.org/pandas-docs/stable/api.html#api-dataframe-stats">statistical functions</a> and <a href="http://pandas.pydata.org/pandas-docs/stable/api.html#id11">plotting functions</a>.


## Advanced statistical analysis

If you need to do something fancier than what pandas offers (and most of us do!), there's most likely a Python library for that.

* <a href="http://www.scipy.org/">scipy</a>: a TON of statistics functions. Check my <a href="http://www.randalolson.com/2012/08/06/statistical-analysis-made-easy-in-python/">blog post</a> for some common useful functions (SEM, bootstrapped 95% confidence intervals, MWW RankSum test, ANOVA, etc.).

* <a href="http://statsmodels.sourceforge.net/">statsmodels</a>: linear regression models, generalized linear regression models, etc. Check here if you need to model your data.

* <a href="http://scikit-learn.org/stable/">scikit-learn</a>: anything machine learning, including data clustering and principle component analysis.

* <a href="http://ipython.org/ipython-doc/dev/config/extensions/rmagic.html">Rmagic</a>: offers support for all R code. If you prefer to use R, or <a href="http://www.randalolson.com/2013/01/14/filling-in-pythons-gaps-in-statistics-packages-with-rmagic/">need an R function that isn't in Python</a>, you can use Rmagic.

From here on out, you're free to explore the example data (or your own). I plan to hold more workshops in the future focusing more specifically on statistical analysis and plotting in IPython Notebook.

<br /><br />

# More useful lessons for scientists

The folks at Software Carpentry have put together a comprehensive set of <a href="http://software-carpentry.org/4_0/index.html">tutorials</a> teaching all kinds of useful computational tools and skills for scientists.
