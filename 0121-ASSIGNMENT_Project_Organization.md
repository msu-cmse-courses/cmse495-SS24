# <center>Project Files - Team Charter and Git Repository</center>

|   |   | 
|---|---|
|![Teams Logo](https://play-lh.googleusercontent.com/jKU64njy8urP89V1O63eJxMtvWjDGETPlHVIhDv9WZAYzsSxRWyWZkUlBJZj_HbkHA)|![Git Logo](https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png)|

This project will use both Microsoft TEAMS and git to organize your files and communications.

1. **_TEAMS FOLDER_** Use this folder to store your team organizational documents. This includes the team charter, project data, meeting minutes, NDA/IP agreements, Weekly 3x3 Reports etc, report drafts, and milestones.

2. **_Git Repository_** Use this folder to track your teams code. We expect all teams to use good software management practices when dealing with code and a good version control system is key.  



-----
# 1. Teams Folder

Your instructor should have already created a folder for your team.  Organize this folder in a way that makes sense to you.  However, you must include files to help the instructors (and your teammates) navigate the folder and quickly find what you need. 

This week we just need you to create a folder for your signed NDA/IP agreements as well as a complete "Team Charter" document from the in-class activity on Wednesday.  As the semester moves forward the structure of your folder should look something like:

    Team_Folder:
        README.docx
        Project_Description.pdf
        Team_Managment_Files
            TEAMNAME_TeamCharter.docx
            Signed_NDA_Agreements.pdf
            Signed_IP_Agreements.pdf
            Weekly3x3
                20240125-3x3.docx
            MeetingNptes
                20240123-Weeky_meeting.docx
        Project_Deliverables
            Propoal.docx
            Proposal_Storyboard.ppt
            Proposal_Video.mp4
            Closed_loop_Storyboard.ppt
            Closed_Loop_Video.mp4
            Final_presntation_Storyboard.ppt
            Final_presentation_video.mp4
            Media_Release.docx
            Project_Slide.ppt
            TEAMNAME_Final_Report.docx
        Individual_TeamMember_files
            Name1
            Name2
            Name3
        Data_Files
            DataFile1.csv
            DataFile2.csv
            

The ```README``` files are extremely important and should be the first "touch point" in your files. Assume that people new to the folders will start there.  Use that to guild people to the other parts of the project.  All files should be documented and clearly labeled.  There should be no confusion about what a file is and why it is in the folder.  The only exception to the previous rule is that anything in the ```Individual_TeamMember_files``` will mostly be ignored.

---

### DO NOT use spaces in file names

When you name all of the files and folders inside of a team directory, please **_DO NOT include spaces_** in the folder or file names.  Although all modern computer's have ways to accept names with spaces do not use them.  Instead use underscores (\_) or ```CamleCase``` (No spaces and capital letters at the beginning of each word in the name).  Avoiding spaces in your names will **_Always_** save time in the long run.  

Points will be taken off if files and folders have spaces in the names. 

### NDA Signatures

If your project requires an NDA or IP agreement. Please make a copy of the correct form for your project and add a picture of your signature to the agreements. The form that is required for your team is in your project team drive.  Sign the document and put a pdf copy in a folder named "Team_Managment_Files" or a "Signed_agreements" folder with your files named "MSUNetID_Team_IP.pdf" and "MSUNETID_Team_NDA.pdf".  For example, I would save mine as "colbrydi_Valve_IP.pdf" and "colbrydi_Valve_NDA.pdf".  

This is an Official document so it is important that you make it look professional.  Some guidelines to consider:

- Remove all yellow highlighting. It is there to show you what you need to edit. 
- Fill out everything you can except the stuff the company will need to fill out. 
- Type everything in except the signature. Do not write information in with a pen.
- If there is a underline space make sure what you type in is also underlined. 
- It is preferred that you actually sign by overlaying a picture of your signature but you can also print out the document, sign it and then scan it.  
- If you use a scanned signature make sure you can't easily tell when looking at the final PDF.  Use a completely white background on your signature. Insert the signature "Underneath" the text so that the singing lines look right. 
- Clean up the spacing so it fits reasonably on the pages. Don't leave dangling lines on extra pages. 

The following video may be helpful if you are confused. Note this video is from a previous semester so the way we are organizing files is different.  The first part about D2L can be ignored (we are using Teams). The rest of the video takes you step by step through me signing the document.

[Direct Link to video](https://youtu.be/amFZNn4NatI)





<iframe
    width="100%"
    height="300"
    src="https://www.youtube.com/embed/amFZNn4NatI?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




### Team Charter

Create a word document, give it a clear name and add it to your Team directory. This will be a "living" document which means it will change as your team grows.  Remember that we drafted this document in class on Wednesday. To start make sure it includes the following:

* Members and roles
* Team Purpose and goals
* Expected outcomes
* Ground rules
* Instructions/URL for accessing the git repository (See below).

For more information about the motivation behind a team charter see the following link:

- [Creating a Team Charter](https://medium.com/@stephenjanaway/creating-a-team-charter-4a94971ab7e1)

---
# 2. Git Repository

Create a git repository and share it with your classmates and instructors.  This repository will be used for the remainder of the course to track all of your code developed for this project. By the end of the semester your repository will have a structure similar to the following:

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
              datafile3.xls
        LICENSE.txt
        makefile
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

Projects structure will vary. The important part is that repositories are well documented so that it is easy to navigate.  You must follow the guidelines shown out in this document.  

Again, the ```README``` file is  extremely important and should be the first "touch point" in your files in your repository. Write the readme in a way that assumes that people reading it know nothing about the project. This means you include a brief description of the class and then guild people to the other parts of the project.  All files should be documented and clearly labeled.  There should be no confusion about what a file is and why it is in the folder.  

### Examples

Here is an example projects you can download from a different course with a similar structure. Note these may have had slightly different expectation and assignment goals relative to your project but are still good representation of the types of projects that would be acceptable for this course.  Projects shared with permission by former students:

- [F19 Neutrino Winds - By Brian Nevins](https://github.com/bnevs88/neutrino-winds)
- [F19 Enhanced sampling Methods - By Nicole Roussey](https://gitlab.msu.edu/roussey1/nmr_fs19_cmse802.git)
- [F19 Visualization of the Transport of Small Molecules on Peptides - By Xie Yan](https://gitlab.msu.edu/xieyan/yanxiecmse802.git)

Even more projects (may require logging into MSU GitLab to access:
- [F19 Lattice QCD Data Analysis - By Matthew Zeilbeck](https://gitlab.msu.edu/zeilbec1/zeilbec1_cmse802)
- [F19 A Tool for Applying Postseismic Corrections to Geodetic Data - By Connor Drooff](https://gitlab.msu.edu/drooffco/cmse-802-drooff.git)
- [F19 OMR Extracter - By Babak Safae](https://gitlab.msu.edu/safaeiba/ocr-omr-reader)




### GitHub vs GitLab vs Other

If your code is under and IP agreement then you are required to use the [MSU Gitlab (https://gitlab.msu.edu)](https://gitlab.msu.edu) server for hosting your private git repository.  This requirement can be waived if you have written permission from the IP owner asking that you use another git service (as long as your instructor has access).  

If your code is not under an IP agreement then your instructors are flexible as to which online git source you use.  Here are things to consider:

- If you want a private repository (i.e. only people you specify can see it) then we suggest the [MSU Gitlab](http://gitlab.msu.edu) server (it is free and secure).
- If you want your code to be public and open then we recommend using [Github](http://github.org) as it is the most popular online git server.
- You can always use more than one service and/or switch later in the semester.  Generally it is easier to start with a secure site such as [MSU Gitlab](http://gitlab.msu.edu) and get less secure than it is to start open and try to make it more secure.

Talk to your instructors if you have any problems.


### Basic git INSTRUCTIONS

For this milestone we only need to set up the basic structure with the following. To start, please keep the files simple and do not include files that do not add something to the project (see "what not to include" below):

    ProjectName/
        .gitignore
        LICENSE.txt
        README.md
            
Here is a description of each of these:

* ```ProjectName``` - The top level folder is the short name of your team. Give your project a short and memorable name. An ideal name should be descriptive and have meaning to people who may be interested in using your software. A poor name only has meaning to your team. For example, **_DO NOT USE CMSE495_** in the the name.  Instead try to pick a name that relates to your project or what you think your project will do.  Although we can change the name later it is much easier if we pick a good name to start. 
    * ```README.md``` - This is a description of your git repository written in Markdown.  For now this file can just contain your team member names.  
    * ```.gitignore``` - There are a lot of files that are inappropriate to include in a git repository (more information below) the "Git Ignore" file helps by telling Git that you never want to use these files.  There are plenty of examples for good ```.gitignore``` files for Python projects on the Internet.  Try to include one that makes sense (you can update it as the semester goes on).
    * ```LICENSE``` - Use this file to describe your license (See section below).  
    
**_HINT_**:  Many of you may find this [git template](https://github.com/colbrydi/CMSE802_Project_Template.git) helpful.
        
If you need help figuring out how to set up your git repository there are a ton of tutorials online. For example here is a good one:

* [git game](https://ohmygit.org/)
* [GitBrancing tutorial](https://learngitbranching.js.org/)
* [Dirk's Full Getting to Know Git Tutorial](https://msu-cmse-courses.github.io/cmse802-f20-student/0000-Getting-to-know-git.html)

If you continue to need help go see your instructors. 





<iframe
    width="100%"
    height="300"
    src="https://www.youtube.com/embed/IAAv4DjYYUA?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




The following video are instructions specifically for how to use the MSU Gitlab.  We will be using the MSU gitlab for all projects because it allows us to best maintain file permissions.  If you have a completely opensource project with no NDA or IP agreement you are also allowed to post on Github or other public spaces:





<iframe
    width="100%"
    height="300"
    src="https://www.youtube.com/embed/6_cegMFG0Pw?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




Some of you may get some sort of "Authentication" error when trying to use git on a windows machine (especially if you have your computer already set up to use github). If that is the case, the following video may help you set up an SSH key on your windows machine.  

- [Direct Link to Windows SSH key generation video](https://youtu.be/b6umB61CV5s)





<iframe
    width="100%"
    height="300"
    src="https://www.youtube.com/embed/b6umB61CV5s?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




As you update and change the files in your repository you will need to push those changes to gitlab.  The following instructions walk you though this process:





<iframe
    width="100%"
    height="300"
    src="https://www.youtube.com/embed/GTM-h5xX2Lk?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




----

### What not to include (building a .gitignore file)

First thing we want to teach is is that not everything should go into a git repository.  i.e. we do not want to bloat our repository with unwanted files.  The git repository works best with Text files that represent "source" code and not compiled or generated code. Here are some basic guidelines of what not to include:


* ```.ipynb_checkpoint``` - These folders are generated when you run jupyter notebooks.  They are "temporary" compiled folders that will change each time you run your notebook and should not be included in your repository. 
* ```__pychache__``` - Similar to .ipynb_checkpoint folders these folders are often generated when running python scripts and should not be included in your repository. 
* **_Other "Temporary" files_** - Temporary files are generated by all types of software and often start with a special characters such as the dot (.) or the tilde (~).  For example many text editors generate temporary files to save a document in case of a program crash.  Do not include temporary files in your repository. 
* **_Compiled Code_** - Programs such as C and FORTRAN must compile their code to an executable in order to run on your computer. These compiled codes are not editable and should be left out of your repository.  Instead it is better to include instructions for compiling the source code as part of your repository.  
* **_Program Output_** - Do not include any program output in your repository (unless for very specific reasons such as documentation, testing, or figures in your final report).  Assume that any output that can be generated by the source code should not be included with the source code (it is redundant). 

A good rule of thumb is that if you did not generate the file and/or do not know what it is you probably do NOT want to include it in your repository. 

**_WARNING_** do not blindly add all files to your repository with the * (star) syntax.  This is bad practice. For example do NOT do the following:

~~```git add *```~~

### Other files to avoid

In addition to the above files it is good to avoid any type of "Binary" file (with a few exceptions).  As stated early, git works best with text files so it can easily track changes. Some example binary files to avoid include:

- **_Large Data files_**  Although it is good to include a few example inputs to your software, avoid using entire datasets.  It is best to store these files someplace else (ex. Teams folder).  
- **_Non-Text formats_** such as Word, Excel or PowerPoint documents should be avoided.  These tend to change each time they are opened even if the core text does not change. it is better to use an alternative text example. 


**_Note:_** one exception to the above rules are image files (ex jpg or png) that are used to help markdown or in the documentation.  It is typically okay to include these since they tend to get included only once and do not change much as the project evolves. 


### .gitignore file

The ```.gitignore``` (read "dot git ignore") file is used to help keep unwanted files out of your project.  Each line ```.gitignore``` file are filenames you want git to ignore.  For example, based on what we said above, a  good place to start on your ```.gitignore``` file would be the following two lines:
```
.ipynbcheckpoint
__pychache__
```

What should go into a .gitignore depends a lot on the type of project.  However, you don't need to invent these from scratch. For example, you could just copy the .gitignore file from the course repository or find one on the internet.





<iframe
    width="100%"
    height="360"
    src="https://www.youtube.com/embed/kzI-mPSY8y4?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




----


### README.md file

Make sure your git repository has a ```README.md``` file.  This file is very important as it will be the first place everyone will look when they first get your repository.  Write this as if someone in the future stumbles across your folder.  Include a brief description of the class, the community partner, the project and the goals of this repository.  Link to any installation instructions or getting started instructions.  It is important that this file guides readers to the rest of the repository. A great resource for writing a well thought out README file can be found here:

<https://readme.so/editor>



----

### Jupyter notebook files in git repositories

Turns out that Jupyter notebook files and git repositories work very poorly together.  Jupyter notebook files are a unique combination of source and program generated information.  So, every time you run a jupyter file it can add output cells which make git think you you changed something important. In many cases it is just a few numbers or some output text.  When you run the ```git status``` command it always looks like jupyter notebook files have changed even when they have not changed. 

A good rule of thumb is to clear all of the output files before committing any changes to jupyter notebook files.  

- Open the jupyter notebook file
- Select "Reset Kernel and clear output" from the menu
- Save the notebook file.
- Do your "git add" and "git commit" commands

The following video goes though why we have to treat jupyter notebooks this way:

[Direct Link](https://www.youtube.com/embed/79hW_TzLos8)





<iframe
    width="100%"
    height="300"
    src="https://www.youtube.com/embed/79hW_TzLos8?cc_load_policy=True"
    frameborder="0"
    allowfullscreen

></iframe>




---

### Licensing file

As authors of software it is important to let people know how they can use our software. ***If your project has an NDA or IP agreement you must copy/paste/edit wording from those file as your LICENSE agreement.***  Please ask during class if you are not sure.  

If you do not have an NDA or IP agreement that covers the License, the following article is a great resource for learning the types of terminology and logic used when talking about software License.  

* https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002598

* https://creativecommons.org/licenses/


![Creative commons license](https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png)

Include a ```./LICENSE``` test file in your top directory. Select which license to use using the following website:

* [https://choosealicense.com/](https://choosealicense.com/)

Copy and paste your chosen license file into a file named ```./LICENSE```

The following articles are a great resource for learning the types of terminology and logic used when talking about software License.  

* https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002598
* [https://choosealicense.com/](https://choosealicense.com/)
* https://creativecommons.org/licenses/

**_Make sure you talk to your instructors to know what type of license is appropriate for your project given.  What license you use may also depend on the NDA and IP agreement made with you and the community partner._**

Include a ```./LICENSE.txt``` test file in your top directory.



# 3. Working with files professionally

Anytime you are working with files you need to pay attention to what you are doing.  Pay attention to whom you will be sharing files and keep things clean and professional.  Points will be taken off for unprofessional files. 

Consider the following guidelines.

---

### Use Filenames that make sense

 Make sure the contents of the files are clear.  If something is associated with a specific date then would like to use the following format:

    YYYYMMDD-TEAM-Contents.ext
    
- ```YYYY``` - Year file (ex, 2023)
- ```MM``` - Two diget Month (ex. 01 for January)
- ```DD``` - Two diget Day (ex. 09 )
- ```TEAM``` - Short team name (if not obvious in context.
- ```Contents``` - Content of the file.

---

### DO NOT use spaces in file names

I said this above and I will say it again. 

When you name all of the files and folders inside of a repository, it is important that your names **_DO NOT include spaces_**.  Although all modern computer's have ways to accept names with spaces do not use them.  Instead use underscores (\_) or ```CamleCase``` (No spaces and capital letters at the beginning of each word in the name).  Avoiding spaces in your names will **_Alaways_** save time in the long run.  

----

### Always Use Relative Paths

In your code there are two basic ways to determine the location of a folder inside your computer; Relative Paths and Absolute Paths.  A relative path is a path starting from your current directory and an absolute path is is a path starting from your computer's "root" directory.  

- Relative paths typically start with a single dot (.), representing the current directory, or two double dots (..) representing the current directories parent folder.
- Absolute paths typically start at the global root directory (/) on a Linux or Mac machine or with a drive label (ex C:) on a windows machine.  

**_ALWAYS_** use relative paths in your git repository.  This ensures that others will be able to use your software if they download it onto their computer.  For example:

    Good: ./data/  or ../data/ is a relative path to a child directory or sibling directory called data. 
    Bad (not acceptable): C:/research/data or /mnt/home/data are absolute paths to a data directory
 
 

---
# 4. Submission

Put all the docents in the required locations.  

If you have an IP and NDA agreement have one (and only one) person from your team email the signed documents to your instructors and your community partners. These MUST be professional emails.  You can ask an instructor to check it before hitting send.  




---
# Evaluation

Project will be evaluated primary looking at following directions.  

Make sure your instructors and classmates have the correct permissions to access, clone your repositories and provide the full git command/instructions in your team charter.  

Your instructor will evaluate your assignment by reviewing the following:

- Review of team charter
- Checking pdfs of NDA and IP agreements (if required)
- Forking and cloning your repository using the link in your team charter
- Verify repository/files are hosted properly per NDA/IP agreements
- Reviewing of your git log
- Review of your repository README file
- Checking your License file
- Checking for reasonable .gitignore file

You will be graded on how well directions were followed and the professionalism of the submission.

Points will be taken off if your signed NDA/IP agreemnts are unprofessional.  

---
# Post-Evaluation

Review feedback from instructors and ensure that any requested changes are made. 

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
