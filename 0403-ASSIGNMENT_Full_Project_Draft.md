# Project Draft

In this assignment you will clean finish up our project structure to make it as easy as possible for others to use.  We have been doing pieces of this all semester but here we will add a few finishing touches to make the project complete. Specifically we need to put in enough structure such that anyone taking the course can get it up and running. This includes: 

1. Installation Instructions
2. Testing Instructions
3. Examples

If you remember from the first project, the structure of the repository should be something like the following:

    ProjectName/
        .gitignore
        docs/
             package_name/
                  module1.html
                  module2.html
             images/
                  image1.jpg
        environments.yml
        Examples/
              datafile1.csv
              datafile2.tiff
              datafile3.xls.
        Figures/
              Generate_Figure1.ipynb
              Generate_Figure2.ipynb
              Generate_Figure3.ipynb
        LICENSE.txt
        makefile
        Reports/
             Meeting_Minutes.md
             Team_Charter.md
             Project_proposal.ipynb
             Closed_loop_Report.ipynb
        package_name/
              __init__.py
              module1.py
              module2.py
              test/
                  __init__.py
                  test_module1.py
                  test_module2.py
        README.md
        setup.py
        Final_Report.ipynb
        

---

# 1. Install instructions

Your project needs to include clear installation instructions with all requirements.  These instructions can be included in your README.md file in the top directory.  

I highly recommend you include instructions for creating a conda environment so that classmates are easily able to run your code. This means they need to temporarily set up their computer with the same settings as your system.  

Ideally you want include a ```environment.yml``` with your project so that other students and instructors can use the following commands to set up the environment:

    conda env create --prefix ./envs --file environment.yml
    conda activate ./envs
    
The ```environment.yml``` file can be created to "copy" your current enviornment by running the following command:

    conda env export --from-history > environment.yml
    
    
Note, try to make your ```environment.yml``` file the minimum packages you will need to run your project.  **_Do not_** create an ```environment.yml``` file on your base anaconda environment as this will just install a lot of stuff that is not needed. A good way to figure out your base install is to create a new environment and add packages until your code works. For example:

    conda create --prefix ./envs pip jupyter pytest pylint pdoc3
    conda activate ./envs

Now just use "conda install" and "pip install" to add all of your project dependencies until it starts working. For example may of you will want to include one or all of the following:

    conda install numpy
    conda install matplotlib
    conda install scipy
    conda install jupyter

When you have it working run the ```conda env export --from-history``` command from above. To deactivate and delete your environment just run:

    conda deactivate
    rm -rf ./envs
    
That should be it!!!
    

> **NOTE FOR INTERNATIONAL STUDENTS** with English as a second language.  If you are running on Windows and your computer's default language is not English you may have trouble with UTF8 errors and the ```environment.yml``` file.  The following line may fix the problem.

    conda env export --from-history | Set-Content -Encoding utf8 environment.yml

---

# 2. Examples

Finally, include example code (jupyter notebooks or similar interface prefered) in an obvious location. Have the example(s) describe and show how to use the software and show some results.  

The example should work "out-of-the-box" with no special commands once your conda environment has been installed. 

-----

### Congratulations, you are done!

Now, you just need to commit and push the project changes to your project git repository. 

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
