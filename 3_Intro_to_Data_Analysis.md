# Intro to Data Analysis Notes

## Anaconda

### Conda Commands

#### Updating Conda and Packages

    conda update conda
    conda update --all
    conda update package_name
	
#### Installing and Removing Packages

    conda install package_name
    conda install numpy scipy pandas
    conda install numpy=1.10
    conda remove package_name
	
Install multiple packages: `conda install numpy scipy pandas`

Specify Version: `conda install numpy=1.10`

Conda automatically installs dependencies for you. 
	
#### If you can't remember the name of a package or environment...

    conda list
    conda list env
	conda env list
    conda search *search_term* (with or without quotes...)
	conda search '*beautifulsoup*'

#### Creating and Removing Environments

    conda create -n env_name list_of_packages
    conda create -n py3env python=3
    conda create -n py python=3.6
    conda env remove -n env_name
	
Most of the commands above can be used from within an environment to install or remove packages or update and search packages...
	
#### Entering and Leaving an Environment

##### On Mac / Linux
	
    source activate my_env
    source deactivate
	
When you're in the environment, you'll see the environment name in the terminal prompt. Something like: `(my_env) ~ $`

The default environment is called `root`.
	
##### On Windows

    activate my_env
    deactivate
	
#### Saving and Loading Environments

You can save the packages to a YAML file with 

    conda env export > environment.yaml
	
`> environment.yaml` writes the exported text to a YAML file environment.yaml. This file can now be shared and others will be able to create the same environment you used for the project.

To create an environment from an environment file use 

    conda env create -f environment.yaml

This will create a new environment with the same name listed in environment.yaml.

#### Sharing environments

When sharing your code on GitHub, it's good practice to make an environment file and include it in the repository. This will make it easier for people to install all the dependencies for your code. I also usually include a pip requirements.txt file using [pip freeze](https://pip.pypa.io/en/stable/reference/pip_freeze/) for people not using conda.

#### Removing environments

	conda env remove -n env_name

#### Note on Python 2 vs. 3

For most of Python's history including Python 2, printing was done like so:

	print "Hello", "world!"
	> Hello world!
	
This was changed in Python 3 to a function.

	print("Hello", "world!")
	> Hello world!

The print function was back-ported to Python 2 in version 2.6 through the `__future__` module:

    # In Python 2.6+
    from __future__ import print_function
    print("Hello", "world!")
    > Hello world!
	
The `print` statement doesn't work in Python 3. If you want to print something and have it work in both Python versions, you'll need to import `print_function` in your Python 2 code.	


## Jupyter Notebooks

### Literate programming

Notebooks are a form of [**literate programming**](http://www.literateprogramming.com/) proposed by Donald Knuth in 1984. With literate programming, the documentation is written as a narrative alongside the code instead of sitting off by its own. In Donald Knuth's words,

> Instead of imagining that our main task is to instruct a computer what to do, let us concentrate rather on explaining to human beings what we want a computer to do.

### How notebooks work

Jupyter notebooks grew out of the IPython project started by Fernando Perez. IPython is an interactive shell, similar to the normal Python shell but with great features like syntax highlighting and code completion. Originally, notebooks worked by sending messages from the web app (the notebook you see in the browser) to an IPython kernel (an IPython application running in the background). The kernel executed the code, then sent it back to the notebook. The current architecture is similar.

The central point is the notebook server. You connect to the server through your browser and the notebook is rendered as a web app. Code you write in the web app is sent through the server to the kernel. The kernel runs the code and sends it back to the server, then any output is rendered back in the browser. When you save the notebook, it is written to the server as a JSON file with a `.ipynb` file extension.

The great part of this architecture is that the kernel doesn't need to run Python. Since the notebook and the kernel are separate, code in any language can be sent between them. For example, two of the earlier non-Python kernels were for the R and Julia languages. With an R kernel, code written in R will be sent to the R kernel where it is executed, exactly the same as Python code running on a Python kernel. IPython notebooks were renamed because notebooks became language agnostic. The new name Jupyter comes from the combination of Julia, Python, and R. If you're interested, here's a [list of available kernels](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels).

Another benefit is that the server can be run anywhere and accessed via the internet. Typically you'll be running the server on your own machine where all your data and notebook files are stored. But, you could also [set up a server](http://jupyter-notebook.readthedocs.io/en/latest/public_server.html) on a remote machine or cloud instance like Amazon's EC2. Then, you can access the notebooks in your browser from anywhere in the world.

### Installing

By far the easiest way to install Jupyter is with Anaconda. Jupyter notebooks automatically come with the distribution. You'll be able to use notebooks from the default environment.

To install Jupyter notebooks in a conda environment, use `conda install jupyter notebook`.

Jupyter notebooks are also available through pip with `pip install jupyter notebook`.

### Launching the notebook server

To start a notebook server, enter `jupyter notebook` in your terminal or console. This will start the server in the directory you ran the command in. That means any notebook files will be saved in that directory. Typically you'd want to start the server in the directory where your notebooks live. However, you can navigate through your file system to where the notebooks are.

When you run the command (try it yourself!), the server home should open in your browser. By default, the notebook server runs at `http://localhost:8888`. If you aren't familiar with this, `localhost` means your computer and `8888` is the port the server is communicating on. As long as the server is still running, you can always come back to it by going to http://localhost:8888 in your browser.

If you start another server, it'll try to use port `8888`, but since it is occupied, the new server will run on port `8889`. Then, you'd connect to it at `http://localhost:8889`. Every additional notebook server will increment the port number like this.

### Closing the server connection

`ctrl+c`

### Shutting down Jupyter

You can shutdown individual notebooks by marking the checkbox next to the notebook on the server home and clicking "Shutdown." 

You can shutdown the entire server by pressing `control + C` twice in the terminal.

### Command palette

The little keyboard is the command palette. This will bring up a panel with a search bar where you can search for various commands. Just open the command palette and type in what you want to do. 

### Kernel type and indicator 

Over on the right is the kernel type (Python 3 in my case) and next to it, a little circle. When the kernel is running a cell, it'll fill in. For most operations which run quickly, it won't fill in. It's a little indicator to let you know longer running code is actually running.

### Saving Notebooks

Along with the save button in the toolbar, notebooks are automatically saved periodically. The most recent save is noted to the right of the title. You can save manually with the save button, or by pressing `Esc` then `s` on your keyboard. The `Esc` key changes to command mode and `s` is the shortcut for "save." 

In the "File" menu, you can download the notebook in multiple formats. You'll often want to download it as an HTML file to share with others who aren't using Jupyter. Also, you can download the notebook as a normal Python file where all the code will run like normal. The Markdown and reST formats are great for using notebooks in blogs or documentation.

### Keyboard Shortcuts

By default, when you create a new cell or move to the next one, you'll be in command mode. 

- To enter edit mode, press Enter/Return. 
- To go back from edit mode to command mode, press Escape

- press Enter + Shift to get to the next cell
- bring up the list of shortcuts by pressing H in command mode
- create a cell above the current cell by pressing A in command mode
- create a cell below the currently selected cell by pressing B
- To change from Markdown to a code cell, press Y
- To switch from code to Markdown, press M
- turn on numbers by pressing L in command mode on a code cell
- Delete cells by pressing D twice in a row so DD
- To save the book, press S
- access the command palette by pressing Shift + Control/Command + P

### Magic keywords

Magic commands are preceded with one or two percent signs (% or %%) for line magics and cell magics, respectively. Line magics apply only to the line the magic command is written on, while cell magics apply to the whole cell.

#### Timing code

You can use the `timeit` magic command to time how long it takes for a function to run.

    %timeit fibol(20)
  
If you want to time how long it takes for a whole cell to run, you'd use `%%timeit` like so:

    %%timeit 
    # rest of your code here in the same cell

#### Embedding visualizations in notebooks

You can use `%matplotlib` to set up matplotlib for interactive use in the notebook. By default figures will render in their own window. However, you can pass arguments to the command to select a specific "backend", the software that renders the image. To render figures directly in the notebook, you should use the inline backend with the command `%matplotlib inline`.

*Tip:* On higher resolution screens such as Retina displays, the default images in notebooks can look blurry. Use `%config InlineBackend.figure_format = 'retina'` after `%matplotlib inline` to render higher resolution images.

#### Debugging in the Notebook

With the Python kernel, you can turn on the interactive debugger using the magic command `%pdb`.  To quit the debugger, simply enter `q` in the prompt.

#### List of all magic commands

<http://ipython.readthedocs.io/en/stable/interactive/magics.html>

### Converting notebooks

Notebooks are just big JSON files with the extension .ipynb.

Since notebooks are JSON, it is simple to convert them to other formats. Jupyter comes with a utility called `nbconvert` for converting to HTML, Markdown, slideshows, etc.

For example, to convert a notebook to an HTML file, in your terminal use

    jupyter nbconvert --to html notebook.ipynb

<https://nbconvert.readthedocs.io/en/latest/usage.html>

### Creating a slideshow

You'll need to designate which cells are slides and the type of slide the cell will be. In the menu bar, click View > Cell Toolbar > Slideshow to bring up the slide cell menu on each cell.

This will show a menu dropdown on each cell that lets you choose how the cell shows up in the slideshow.

**Slides** are full slides that you move through left to right. **Sub-slides** show up in the slideshow by pressing up or down. **Fragments** are hidden at first, then appear with a button press. You can skip cells in the slideshow with **Skip** and **Notes** leaves the cell as speaker notes.

Running the slideshow
To create the slideshow from the notebook file, you'll need to use nbconvert:

    jupyter nbconvert notebook.ipynb --to slides
    
This just converts the notebook to the necessary files for the slideshow, but you need to serve it with an HTTP server to actually see the presentation.

To convert it and immediately see it, use

    jupyter nbconvert notebook.ipynb --to slides --post serve

This will open up the slideshow in your browser so you can present it.




