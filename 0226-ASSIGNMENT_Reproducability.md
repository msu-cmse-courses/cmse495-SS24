# Project Reproducibility

![Logo representing four seasons which is intended as an analogy for environments used to reproduce software](https://freesvg.org/img/Four-season-symbols.png)

- [Image from freesvg.org](https://freesvg.org)

In this project your team will produce a clear set of instructions to easily install and demo (test) the required software to reproduce the results for your project.  By following these directions your instructor and sponsors should be able to install everything that is necessary to get your experiments running.  

Most project this will mean including an ```INSTALL.md``` file in your main git director and maybe an ```environments.yml``` or ```requirements.txt``` file.  In any case the instructions should be short, clear and have a minimum number of steps.  


# Deliverables 

Teams must add a instructions on how to install the software, download example data and test run the code for their project. This should be complete instructions with all required steps and helpful hints if there are problems. Make sure the instructions are also simple without requiring extra libraries that are not used. 

Make sure it is clear where your instructions are located.  Adding a line in your ```README.md``` file is probably a good idea.

# Example

An ideal project will have a at most one or two commends needed to install and run everything.  Your instructor really prefers conda environments but teams can also use a pip install command (or something similar in other languages) with a ```requirements.txt``` file.  Here might be a typical set of instructions:

1. Download and install the miniconda software for your OS. Follow default install instructions. ([link to miniconda](https://docs.conda.io/en/latest/miniconda.html))
2. Clone or unzip the project repository into a folder on your computer.
    ```git clone <<PROJECT URL>>```
3. Open an anaconda command prompt and navigate to the project folder.  
4. Create a project specific conda environment by running the following command from the unzipped folder ```conda env create --prefix ./envs --file environment.yml```
5. Activate the conda environment using the following command ```conda activate ./envs```
6. Start Jupyter using the following command ```jupyter notebook```
7. From Jupyter open the ```demo.ipynb``` file and continue the instructions from there.

My sure your instructions are tailored to your audience.  Some projects may need multiple sets of instructions i.e. ones for the instructor and ones for the sponsors.  More is often better as long as they are clear and easy to understand. 

# Submission

Add your files to your team git repository on or before the deadline.  

**_NOTE_**: We will be sharing the installation instructions with your classmates. Make sure there is a way to install and test the instructions without violating your NDA. If there is a problem please notify your instructors. 

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
