# IPython Notebook Installation Instructions


## Windows

Make sure you're starting with a clean install. Remove any Python installs you installed previously. Delete the `C:/pythonx.x` folder.

### Enthought Python Distribution

Download the free version of the Enthought Python Distribution (EPD): http://www.enthought.com/products/epd_free.php

Install EPD into the default directory it suggests.

You now have IPython and most of the libraries you need installed. However, they're mostly older versions, so let's update them real quick.

### Distribute library

The `Distribute` library is required for the newer version of IPython Notebook.

Go to http://python-distribute.org/distribute_setup.py

Right-click and save the file to `C:/Users/your-username/`

Open up the Windows Command Prompt and enter the following command: `python distribute_setup.py`

### pyreadline library

Download the pyreadline library: http://pypi.python.org/packages/any/p/pyreadline/pyreadline-1.7.1.win32.exe#md5=ffe3987562d0891901ebccdd94933a39

Install it to the default install location.

Install the `readline` library as well by entering the following command into the Command Prompt: `easy_install readline`. If it asks you if you want to run the executable, click Yes.

### pandas library

pandas isn't required for IPython Notebook, but it's the best library in Python for handling data.

Enter the following command: `easy_install pandas`. If it asks you you want to run the executable, click Yes.

### Update IPython

Now, let's get the latest version of IPython so we have the latest and greatest features. Enter the following commands into the Command Prompt, one at a time.

	git clone https://github.com/ipython/ipython.git
	cd ipython
	python setupy.py build
	python setup.py install
	cd ..
	rmdir /s ipython

### Run IPython Notebook

Now you should be ready to enjoy IPython Notebook! Enter the following command in the Command Prompt to fire it up: `ipython notebook --pylab=inline`



## Mac and Linux

### Enthought Python Distribution

Download the free version of the Enthought Python Distribution (EPD): http://www.enthought.com/products/epd_free.php

Install EPD into the default directory it suggests.

### Update IPython

You now have IPython and most of the libraries you need installed. However, they're mostly older versions, so let's update them real quick.

Enter the following commands into the Terminal, one at a time:

	sudo easy_install pandas
	
	git clone https://github.com/ipython/ipython.git
	cd ipython
	python setup.py build
	python setup.py install
	cd ..
	rm -r ipython

### Run IPython Notebook

Now you should be ready to enjoy IPython Notebook! Enter the following command in the Terminal to fire it up: `ipython notebook --pylab=inline`


# Practice Statistical Analysis

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


## Statistical analysis

If you need to do something fancier than what pandas offers (and most of us do!), there's most likely a Python library for that.

* <a href="http://www.scipy.org/">scipy</a>: a TON of statistics functions. Check my <a href="http://www.randalolson.com/2012/08/06/statistical-analysis-made-easy-in-python/">blog post</a> for some common useful functions (SEM, bootstrapped 95% confidence intervals, MWW RankSum test, ANOVA, etc.).

* <a href="http://statsmodels.sourceforge.net/">statsmodels</a>: linear regression models, generalized linear regression models, etc. Check here if you need to model your data.

* <a href="http://scikit-learn.org/stable/">scikit-learn</a>: anything machine learning, including data clustering and principle component analysis.

From here on out, you're free to explore the example data (or your own). I plan to hold more workshops in the future focusing more specifically on statistical analysis and plotting in IPython Notebook.
