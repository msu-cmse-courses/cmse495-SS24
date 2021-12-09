# <center>Stub Functions and Automatic Documentation</center>

<img src="https://pdoc3.github.io/pdoc/logo.png" width=30% alt="Sphinx logo">


The goal of this project is to solidify and document the major structure of your project code.  We will do this by adding stub functions (where needed) and using an automatic documentation tool (ex. [pdoc3 automatic documentation generator](https://pdoc3.github.io/pdoc/)).  An automatic documentation generator takes comments formated in your source code and uses them to generate your project documentation.  This way you only need to change one set of files.  

**Note:** although your instructor was able to get pdoc3 running on Jupyterhub the steps are much easier if you run from your local Anaconda install. We highly recommend using the local install. If you are not using python you must find the appropriate automatic documentation for your language. 

# Stubbing out your code

A stub function in software development is like an outline used to stand in as a substitute before the details of the function can be completed.  Good stub functions are like a plan for what you want your code to do. It takes the expected inputs and returns outputs in the expected format.  

For this project we want to stub out the main structure of your programming interface.  How the functions are stubbed out will depend highly on your project.  The idea is to plan how you want the code functions and libraries to interact before writing in all of the details.  Good stubbing will make it much easier to incrementally develop and test your project code.  

&#9989; **<font color=red>DO THIS:</font>**  Stub out the main functions and classes for your code.  Commit your changes to your git repository.

# Docstrings

The Python programming language has some standard ways that functions and classes should be documented.  Strings surrounded by triple quotes (""") located at the beginning of documents, functions and classes are used to document those items.  Consider the following example function:

Docstrings are the primary way that Python uses to print ```help``` messages. For example:

    Help on function testfunction in module __main__:
    
    testfunction(a, b)
        This is a test funciton documentation
        You can put your stuff here
    


&#9989; **<font color=red>DO THIS:</font>**  Read the [PEP257](https://www.python.org/dev/peps/pep-0257/) standard and write docstrings for all of your files, functions and classes. Commit your changes to your git repository. (another good resource is  [this post on DocStrings](https://www.datacamp.com/community/tutorials/docstrings-python))

&#9989; **<font color=red>DO THIS:</font>**  Install and use [```pydocstyle```](http://www.pydocstyle.org/) to check and ensure the documentation meets the PEP257 standard as best it can. Commit any additional changes to your git repository. See instructions in next section for example installation code. 

    conda install pydocstyle
    pydocstyle modulename

# Automatic Documentation using [```pdoc3```](https://pdoc3.github.io/pdoc/)

The ```help``` function is not the only Python module that can take advantage of doc strings.  There are a class of programs called "auto documentors" that can read though code, organize the doc strings and output documentation for your software in a variety of formats (ex. pdf and html).  Probably the most famous of these is [Sphinx](http://www.sphinx-doc.org/).  However, ```Sphyix``` is really intended for large software projects and is a little overkill for our class project.  For this project we plan to use ```pdoc``` which is a much easier to use program and fully compatible with ```Sphyix```. Meaning we can use ```pdoc``` to organize our documentation and easily upgrade to ```Sphyix``` if/when that is deemed necessary.  

Make sure you install ```pdoc3``` for use in your project.  Older versions of ```pdoc``` are much harder to use. Here are some commands to get it working (hopefully these commands are familiar to you by now):

    conda install pdoc3 
    pdoc --force --html --output-dir ./docs modulename

&#9989; **<font color=red>DO THIS:</font>** Get ```pdoc3``` working with your project code and generate html files in a docs folder using the above.  Commit the html files to the folder and push all of your changes to your git central repository. **_HINT_** Use the ```make docs``` command to run pdoc3 on your repository.

---
### Getting credit for your assignment

Now, you just need to commit and push this report to your project git repository. Your instructor will download your repository and check your automatic documentation using the ```make docs``` command so make sure that is working. 

-----
### Congratulations, you are done!

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
