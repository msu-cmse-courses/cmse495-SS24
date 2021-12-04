# <center>Delinting (linting) your code</center>

<img src="https://lh4.googleusercontent.com/i0hZKXrihnUtlAQM6Hb89zo296lPckUN7FVMGih3D7z9WjueaImCXd98pAHA4GzHMrTFLglWqbGa2OxyDa2Y7ihp18ljIiaLIaHwNZSA4sRre3RRxrDcFj2FIv0c=w224" width=20% alt="pyTest logo">

The goal of this assignment is to make your project code much easier to read by following a style guild and using lint and delint tools to clean up the code. 

----
<a name="Style_Guild"></a>

# 1. Pick a Style Guild

&#9989; **<font color=red>DO THIS:</font>**  Find a review a style guild for your project's programming language.  Make sure you clearly document which style guild you are using.  For example, in python the pep8 style guild is the standard used by the core libraries: 

### Python Enhancement Proposal Eight:
* [PEP 8 -- Style Guild for Python](https://www.python.org/dev/peps/pep-0008/)
* [A little cleaner pep8 guild](https://pep8.org/)


# 2. Update code to match Style guild

Once you have picked a style guild update your code to match the style. Not everything needs to match perfectly but we want to get as close to possible.  

----
<a name="Installing_linters"></a>

# 2. Lint software

There are many tools out there that are designed to identify "lint" in your code. these are not errors but are violations of a style guild.  Identify a linting tool and include instructions for installing and running the tool in your repository.  

For example, in python we often use ```pylint``` on your entire python project folder (including test files).  This will return a list of linting errors and a lint score you can use to improve your code(officially it is a scale from 0-10 but weirdly you can get negative numbers).  Report a lint score as part of the report for this Assignment. A lint score may just be a count of the number of lint errors found by the tool.  If you have trouble finding a linting tool for your programming language you must talk to the instructor early. 


----
<a name="Autopep8"></a>

# 3. Automatic Delinter

When you use a common style guild there are tools that can automatically modify your code to try to match the style (and thus lower your lint score). These tools can be amazing. Try to find one for your programming language and include install and running instructions for this assignment.  Try to evaluate how well the delinter worked for your project.

For example, ```autopep8``` is a delinter for python (there are others). 

----
<a name="Manually_lint_your_code"></a>

# 4. Manually lint your code

&#9989;**<font color=red>DO THIS:</font>** Modify your code to improve your lint score (lower the number of lint errors). For example, a good goal in python is a ```pylint``` score of 5-10.    


---
### Getting credit for your assignment

Commit all of your code changes and push them to your project git repository on or before **11:59pm on Sunday March 27**. Your instructor will download your repository and check your lint by following the linting instructions in your README file.

----
Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
