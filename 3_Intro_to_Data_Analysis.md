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
	
#### If you can't remember the name of a package or environment...
	conda list
	conda list env
	conda search search_term

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
	
##### On Windows

	activate my_env
	deactivate
	
#### Saving and Loading Environments

You can save the packages to a YAML file with 

	conda env export > environment.yaml
	
`> environment.yaml` writes the exported text to a YAML file environment.yaml. This file can now be shared and others will be able to create the same environment you used for the project.

To create an environment from an environment file use `conda env create -f environment.yaml`. This will create a new environment with the same name listed in environment.yaml.

#### Sharing environments

When sharing your code on GitHub, it's good practice to make an environment file and include it in the repository. This will make it easier for people to install all the dependencies for your code. I also usually include a pip requirements.txt file using pip freeze for people not using conda.


## Jupyter Notebooks

### Literate programming

Notebooks are a form of **literate programming** proposed by Donald Knuth in 1984. With literate programming, the documentation is written as a narrative alongside the code instead of sitting off by its own. In Donald Knuth's words,

> Instead of imagining that our main task is to instruct a computer what to do, let us concentrate rather on explaining to human beings what we want a computer to do.

After all, code is written for humans, not for computers.

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

