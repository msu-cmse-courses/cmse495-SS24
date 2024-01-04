# Project Reproducibility

![Logo representing four seasons which is intended as an analogy for environments used to reproduce software](https://freesvg.org/img/Four-season-symbols.png)

- [Image from freesvg.org](https://freesvg.org)

In this project your team will produce a clear set of instructions to easily install and demo (test) the required software needed for your project. By following these directions your instructor and community partner should be able to install everything that is necessary to get your experiments running.  

You will be expected to share the installation instructions with your classmates. At some point you will need to make sure there is a way to install and test the instructions without violating your NDA. One way to do this is to provide example data that does not come from the community partners.  If there is a problem please notify your instructors now.


---

# Installation instructions

The location of the installation instructions will vary based on the language and tools being used. For most project this will mean including an ```INSTALL.md``` file in your main git directory and maybe an ```environments.yml``` or ```requirements.txt``` file.  In any case the instructions should be short, clear and have a minimum number of steps.  Make sure you include the following:


## Data Instructions
Since data is typically ***NOT*** included in a git repository (except for small example files) the instructions should clearly be written such that both the community partners and the instructors know where to locate the data and where to put the data relative to the code.  Use relative paths and not absolute paths to ensure portability of the instructions.

## Software Install Instructions
The instructions should include a list of all software/packages needed to reproduce the results.  These should include basic instructions for downloading and installing. 

If using python or R it is highly recommended that the team includes instructions for creating a conda environment so that classmates, community partners and instructors are easily able to run the code. This means they need to temporarily set up their computer with the same settings as your system.  

Ideally you also want include a ```environment.yml``` with your project so that other students and instructors can use the following commands to set up the environment:

    conda env create --prefix ./envs --file environment.yml
    conda activate ./envs
    
The ```environment.yml``` file can be created to "copy" your current environment by running the following command:

    conda env export --from-history > environment.yml

Note, try to make your ```environment.yml``` file the minimum packages you will need to run your project.  **_Do not_** create an ```environment.yml``` file on your entire base anaconda environment as this will just install a lot of stuff that is not needed. A good way to figure out your base install is to create a new environment and add packages one-by-one until your code works. For example:

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
    
Test your install instructions on more than one computer.  Try to make them as robust as possible so that the instructor does not need to figure out what is missing.  

> **NOTE FOR INTERNATIONAL STUDENTS** with English as a second language.  If you are running on Windows and your computer's default language is not English you may have trouble with UTF8 errors and the ```environment.yml``` file.  Running the following line on a windows command prompt in your git repository directory may fix the problem.

    conda env export --from-history | Set-Content -Encoding utf8 environment.yml

## Demo Code

Finally, include example code (jupyter notebooks or similar interface preferred) in an obvious location. Have the example(s) describe and show how to use the software, preview your end-to-end solution and show some preliminary results.  

The example should work "out-of-the-box" with no special commands once your core software has been installed. Make sure this software is well documented. If your team is using Jupyter notebooks make sure you use proper syntax. 

This demo doesn't need to include finished details of the data/results but should provide a preview of all of the steps you are expecting in your end project for instructors to make sure the install worked and that everything will be ready for the community partners. 

# Deliverables 
Make sure it is clear where your instructions are located.  The ```INSTALL.md``` file is a good place to start but consider adding a line in your ```README.md``` file linking to the ```INSTALL.md``` file.

# Example

An ideal project will have a at most one or two commends needed to install and run everything.  Your instructor really prefers conda environments but teams can also use a pip install command (or something similar in other languages) with a ```requirements.txt``` file.  Here might be a typical set of instructions:

1. Clone or unzip the project repository into a folder on your computer.
    ```git clone <<PROJECT URL>>```
2. Copy the data files stored in ```/path/``` teams folder into the empty "data" directory inside the cloned repository.
3. Download and install the miniconda software for your OS. Follow default install instructions. ([link to miniconda](https://docs.conda.io/en/latest/miniconda.html))
4. Open an anaconda command prompt and navigate to the project folder.  
5. Create a project specific conda environment by running the following command from the unzipped folder ```conda env create --prefix ./envs --file environment.yml```
6. Activate the conda environment using the following command ```conda activate ./envs```
7. Start Jupyter using the following command ```jupyter notebook```
7. From Jupyter open the ```demo.ipynb``` file and continue the instructions from there.

My sure your instructions are tailored to your audience.  Some projects may need multiple sets of instructions i.e. ones for the instructor and ones for the community partners.  More is often better as long as they are clear and easy to understand. 

# Submission

Add your instruction files to your team git repository on or before the deadline. 


# Evaluation

Instructor will clone (or do a pull) to get the most recent copy of your repository.  They will conduct a code review starting with the README file and then attempt to follow the INSTALL instruct. Points will be taken off for unclear steps. Instructor will provide feedback to help you achieve the balance between incomplete and overly detailed. 

# Post-Submission

Review the feedback from your instructors and make necessary changes to the instructions based on the feedback. 

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
