# Anaconda-Jupyter-installtion

# Installation of the Python ecosystem
We chose Python due to several reasons. First, our choice reflects the current trends and demands in data science, and in programming overall.

If we look at the number of questions asked on Stack Overflow, THE question and answer site for professional and enthusiast programmers, separated by the different programming languages used in the data science domain, we can see the following overall trend:

![](https://i.imgur.com/gafdLxp.png)


As you can see, since 2013, Python’s presence has continuously increased and it has become the most used (or asked about) data science programming language since already a few years.

Second, Python is easy to learn and use. Python code is famous for being clean and readable and is considered by many as very beginner friendly, especially if you are already familiar with a programming language. Moreover, if you have previous experience in any of Java, C/C++, Matlab or even Excel, you will find Python syntax very accessible.

And finally, Python is very versatile. When we think of the main data analysis tasks that we would perform with other tools, there is almost always an equivalent way to do it in Python. For example, we can do a similar numerical analysis to Matlab using the Python package [NumPy](https://numpy.org/), and we have the same plotting functionality with the [Matplotlib](https://matplotlib.org/) package. In comparison to R, we can find similar machine learning algorithms in the [Scikit-learn](https://scikit-learn.org/stable/) package, as well as data manipulation techniques in the [Pandas](https://pandas.pydata.org/) one.

When it came down to it, we wanted to pick a language that we could teach the entire program with, and that would give the biggest value to an aspiring data scientist. Python was the obvious choice.

Now that you are hopefully convinced why Python is a great language for data science, let’s start by setting up the essential Python programming environment. For the installation process, we will be working from the terminal window: this is the Terminal application for Mac and Linux, and the Anaconda command prompt for Windows.

The following steps will guide you through this process.

## Step 1: Download Anaconda
We will use Anaconda to automatically handle all the Python installation and management for us. Anaconda is a distribution of software that comes with **Conda, Python**, and many **scientific packages** that we will be using for data science.

> We don’t install libraries, we install packages which contain the libraries pre-built for our specific system.

To download Anaconda, go to anaconda.com/download and download the Python 3.x version. For specific instructions on how to install Anaconda for macOS, Windows, or Linux you can consult docs.continuum.io/anaconda/install.

### Warning
> **For windows users**: We’ve seen that the newest version of Anaconda can create some issues on Windows machines. These issues are only restricted to anaconda and lead to the error popup message “python.exe - Entry Point Not Found” and that “pythoncom39.dll” cannot be found.
> 
> To prevent this message and have anaconda and Jupyter running without any issues, we recommend to download a previous anaconda version (which is listed on [this page](https://repo.anaconda.com/archive/))

### Note
> When installing Anaconda, we automatically get Python, Conda, and 150 of the most popular Python packages for science, math and data analysis.

> If we want a lighter alternative to Anaconda for a faster installation, or we want to manage the package installation ourselves, we can instead use Miniconda which comes with only Python and Conda. Miniconda can be downloaded from [conda.io/miniconda.html](https://docs.conda.io/en/latest/miniconda.html). If you choose to install Miniconda instead of Anaconda, make sure to download the Python 3.x version for your system.

## Step 2 - Download the environment file
When starting a new Python project, it’s always a good idea to create a **virtual environment** specifically for the project. We can think of an environment as an isolated copy of Python that maintains its own files and directories. This makes working on multiple projects much less troublesome by ensuring that each project is cleanly separated and there are no problems with dependencies between them.

The nice thing about Anaconda is that it comes with **Conda**: a package and **environment manager** that we can use to create environments for our projects. To create the Conda environment, we will use a .yml environment file which contains the list of packages that you need for this course with their version number. You can download it from the resource section of this unit.

* Download the [`adsml.yml.zip`](https://drive.google.com/file/d/1IQiizPg631buCY0OPIiSNB3TsQ8SNzKP/view?usp=sharing)
* Extract the archive on your computer
This file tells Conda which libraries to download and most importantly which versions. Setting up your environment with this file will ensure that you are using the same versions as these course notes which is important for ensuring that you will have the same outputs. To get the list of installed libraries and their versions, you can take a look at the `.yml` file by opening it with a text editor.

## Step 3 - Create the environment
We will now type a few commands to install the course environment using the .yml file.

* If you are on macOS and Linux: open a Terminal application.
* If you are on Windows: open the Anaconda command prompt from the Start menu.


If you correctly installed Anaconda or Miniconda in step 1, you should be able to list the current Conda environments available on your machine by typing the following command

```
conda env list
```
**Troubleshooting**: If this command doesn’t work for you, then it’s likely that your terminal doesn’t find conda. In that case, verify that you have Anaconda or Miniconda installed.

If you didn’t previously install any Conda environment, it should only display the default one called **base**, or sometimes **root**, along with its installation path which may vary depending on your machine and whether you installed Anaconda or Miniconda.

```
# conda environments:
#
base                  *  C:\Users\user\anaconda3
```
Before installing the course environment, make sure you have an up-to-date version of conda by running

```
conda update conda
```
Note that you can always retrieve Conda’s version with

```
conda -V
```
and then verify that the release is a recent one on this page: List of Conda releases

Let’s now **create the environment** by running the following command.

```
conda env create -f adsml.yml
```
Note that you need to be in the same folder as the adsml.yml file to run this command.

**Troubleshooting**: If you cannot locate your `.yml` file from the terminal or the Anaconda prompt, use the File Explorer to find its absolute path. Open the explorer and go to the file (ex. in your Downloads folder), right click on it and open the details window. You should be able to copy/paste the absolute path from there and use it in the command:
```
# On Windows, it will look something like
conda env create -f C:\Users\your_username\Downloads\adsml.yml
# On macOS
conda env create -f /Users/your_username/Downloads/adsml.yml

```
After installing the course environment, you should see an adsml entry in the list of available environments - this is the course environment that we will use for the exercises and projects.

```
conda env list

# conda environments:
#
base                *  C:\Users\user\anaconda3
adsml                  C:\Users\user\anaconda3\envs\adsml
```
## Step 4 - Work with the course environment
Let’s now try to run a few commands in Python using the course environment. First, in the terminal (mac, linux) or Anaconda command prompt (windows), activate the course **environment** by running

```
conda activate adsml
```
Everything that we run from the terminal will now use the course environment. Let’s try to run a few Python commands via the [IPython](https://ipython.org/) interactive interface. Start it by typing

```
ipython
```

The command should start an **IPython session** and let you type any Python commands after In [1]:

```
Python 3.9.2 | packaged by conda-forge | (default, Feb 21 2021, 05:02:20) 
Type 'copyright', 'credits' or 'license' for more information
IPython 7.22.0 -- An enhanced Interactive Python. Type '?' for help.
```
You should also see in the message above the` In [1]:` line the exact Python version that the course `.yml` environment file installed. The message can vary, but the Python version should be `3.9.x`

Let’s now run a few Python commands. First, let’s import the [Seaborn](https://seaborn.pydata.org/) library with the `import` Python statement. **Seaborn** is a data visualization library, but we will now use it to import one of its pre-loaded datasets.

```
import seaborn as sns
```
After running this command, the IPython interface will let you enter a second command after `In [2]`:

**Troubleshooting**: If you get a `ModuleNotFoundError `saying `No module named 'seaborn'`, it means that Python cannot find the Seaborn library. Did you start IPython from the `adsml` course environment?

Let’s now import the **Titanic dataset** which contains information about the passengers of the Titanic. We will use the `load_dataset()` function from Seaborn to retrieve the data, and store the results in a data variable.

```
data = sns.load_dataset('titanic')
```
You can now print the data about the first five passengers with:

```
data.head(5)
```
![](https://i.imgur.com/wiRK3yO.png)

To end the IPython session, you can run `exit()` which will get you back to the terminal or Anaconda command prompt. Note that you are still in the course environment.

When you are done working with the `adsml` course environment, you can simply close the terminal window, or return to the `base` environment with

```
conda activate
```
## Step 5: Work with Jupyter notebooks
It’s part of the data science work to produce step-by-step well-documented analyses that can be shared and reproduced. In this program, we will use **Jupyter notebooks** to write and document our analyses. We will learn more about them in this course, but in short, notebooks are a way to organize our work by arranging **code and text cells** into a single `.ipynb` file (IPython notebook) which can then be published into several formats (web pages, PDFs) but also executed and modified by other data scientists.


> Jupyter notebooks are not specific to Python - they can be used to run code in other programming languages such as R, C++, Julia and many others. You can find a list of available languages on [this page](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels).

The most common tool to work with Jupyter notebooks is the **Jupyter Notebook interface**. However, another project called **JupyterLab** will eventually replace it. We installed both via the adsml.yml course environment file, so you can really switch between each interface and use them interchangeably when working with the course exercises and projects.

Before creating our first notebook with JupyterLab, let’s activate the course environment such that we can use all the libraries from it. Open a terminal and run:

```
conda activate adsml
```
To start the JupyterLab interface, you can use the jupyter command:

```
jupyter lab
```
> If you want to use the **Jupyter Notebook interface** (instead of JupyterLab), simply replace lab by notebook in the previous command.

You should see the application opening up in your default web browser. The main window should look like this:

![](https://i.imgur.com/ydY0Tdr.png)


This is what is known as the main work area. On the left-hand side, we have a collapsible sidebar that shows the contents of our home folder (which may differ from the content of your home folder). At the top, we have a menu bar showing the different actions available. And in the very center, we have an area containing tabs for opening a new document.

Let’s select Python` [conda env:adsml]` under the Notebook tab. This will open a Notebook using the course environment. Notebooks are the main type of document that we will work with. It should look like this:

![](https://i.imgur.com/uiyM1iP.png)


All of our work will be produced in these notebooks. One of the great advantages of notebooks is that they allow to combine code, computational output, explanatory text and multimedia all in one place.

Let’s give our notebook a name. We can do this by right-clicking on the `Untitled.ipynb` notebook entry in the left pane and choosing `Rename notebook` from the drop down menu. Type in sample_notebook and hit enter. Your updated view should look like this

![](https://i.imgur.com/regm8F1.png)


If you open your working directory (the directory where you launched JupyterLab from) you will notice that it now contains a new file called `sample_notebook.ipynb`. Once we have a notebook file on our computer we can always open it inside JupyterLab by navigating to its location with the left pane and double-clicking on the file. Don’t worry too much about the ins and outs of the Jupyterlab interface for now since we will cover them in full detail in a future subject.

Now what you see at the very top of the notebook is what we call a cell. It represents an executable block of code. Let’s type in the code to load and display the titanic data

```
import seaborn as sns
data = sns.load_dataset('titanic')
data.head(5)
```
Your notebook should now contain a single cell with the code.

![](https://i.imgur.com/iDZ1S6x.png)


We can now run it by executing the cell. This can be done by pressing the play button ▶️ from the menu or even simpler by pressing Shift+Enter (make sure that the cell is active first, meaning that your cursor is inside it).

Whichever way you choose to execute the cell, the Python code inside the cell will be run and the output of the code is displayed immediately below the cell. Your notebook should now look like this

![](https://i.imgur.com/eYSKrvU.png)


There you go, you just created your first Jupyter Notebook. Don’t forget to save it!

We will go into more detail about Jupyterlab shortly. Before that, we make a small detour to reinforce some basic Python 3 concepts just to make sure that we are all on the same page.

