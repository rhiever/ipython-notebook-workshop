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

Right-click and save the file to `C:/Users/your-username/`.

Open up the Windows Command Prompt and enter the following command: `python distribute_setup.py`.

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
	python setupy.py build
	python setup.py install
	cd ..
	rm -r ipython

### Run IPython Notebook

Now you should be ready to enjoy IPython Notebook! Enter the following command in the Terminal to fire it up: `ipython notebook --pylab=inline`
