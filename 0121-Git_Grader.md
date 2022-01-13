# In-Class Assignment: Git Log Data Collection

![Silhouettes of people with the words "teamwork" underneath](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcdn.pixabay.com%2Fphoto%2F2015%2F10%2F04%2F16%2F45%2Fteam-971343_640.png&f=1&nofb=1)
> Free image from pixabay

In class today we are going to try an experiment to write some code as a team.  We will take a problem and divide it up into parts. Each person or sub-groups of people will work on their part and then we will try to compile them as a group and see if they all work together.  

Everyone will be given 2 class periods (today and next Friday) to finish this project and teams will present their work at the end of the second class.  


## Agenda (80 Minutes)

- (20 minutes) Team Charter
- (60 minutes) Group Programming Project

----

# 1. Team Charter

Reminder, the [Team Charter assignment](0123-ASSIGNMENT_Team_Chater) is due on Sunday

----
<a name="Group_programming_Project"></a>
# 2. Group Programming Project

### Project description

A git repository keeps track of individual authors and their changes. We want to write a program to evaluate the contribution of authors in a git repository for grading.  This will involve, generate a list of all of the contributors, measure each authors contribution and graphing the results. 

The course instructor has broken the project down the following programming components:

1. [Make a list of git contributions (```log```)](#S1)
2. [Measure the magnitude of a contribution (```diff```)](#S2)
3. [Summarize the contribution of each author (```grade```)](#S3)
4. [Graph the results suitable to inform a grade decision (```graph```)](#S4)
5. [Management Group](#S5)

Assuming we get all of these steps written as functions we could imagine a program running from inside a git directory using the following syntax (or something similar):

```python
from group1 import git_log
author_table = git_log() #Convert the output of "git log" command to a pandas table.

from group2 import git_diff
hash1 = author_table['Hash'][0]
hash2 = author_table['Hash'][1]
nlines = git_diff(hash1, hash2)  # Show the number of lines for an individual hash contribution.

from group3 import git_grade
authors = git_grade(author_table) # Generate a list of authors and their contribution for a repository.

from group4 import git_graph
git_graph(authors) # Graph the results in a meaningful way. 
```

Where each of the variables are of the following types:

- ```author_table``` - Pandas table with entries for Author, Date, Hash, and Comment.
- ```nlines``` - number of lines changed by the entry provided as an integer. 
- ```authors``` - dictionary with tag for author names and values of their number of total lines.

### Forming Teams

We are going to try to write each component of our software separately and then assemble them as a team.  The instructor has assigned each group into the following teams:

|   | Team A | Team B|
|---|--------|-------|
| **_Management_** | AFRL | Delta Dental |
| **_git_log_** | Argonne | Ford |
| **_git_diff_** | QSIDE |  Hope Village | 
| **_git_grade_** | Kelloggs | Neogen |
| **_git_graph_** | Boeing  | Old Nation |

&#9989; **<font color=red>DO THIS:</font>** There are two breakout rooms set up (one for Team A and one for team B).  Please join the breakout room for your team and conduct a short meeting.  

1. Identify the members of the Management group
2. Have someone from the management group create a Zoom room with individual breakout rooms for the four working groups (The management group will stay in the main breakout room).  
3. Share the zoom room URL with everyone on the team (do not switch yet).
4. Return to the main room and share your team's zoom room with the rest of the class.

We should now have three zoom rooms you can use. **_Make sure you have all three written down someplace!!!_**  The main course zoom room, Team A zoom room and Team B zoom room. 

&#9989; **<font color=red>DO THIS:</font>** Once you have noted all three zoom rooms.  Join your teams room zoom room, get into your group's breakout room and start working. 


For the groups in charge of generating code you should focus on doing the following: 

1. Have all of your members read though this entire document to see how your part of the project will fit in with other parts of the project. 
2. Write a stub function for your part of the code. A stub function provides the inputs and outputs in a format that can be tested by the other groups. The groups need to agree and share stub functions using the git repository. **_NOTE:_** Make sure you get this done first before writing your main program.  
3. After each step graph or plot the output to make sure it is in the expected form.  
4. Write some test functions that send different data into your function and make sure it works as expected.
5. Update your stub function with the final version in the git repository. 

Key to the success of this project is careful communication between the groups.  If a group gets done early and join the management group to help each other out. Good luck!


----
<a name="S1"></a>
## Group 1: Make a list of git contributions (```log```)

```python
author_table = git_log()
```

This group's job is to write a function that parses the output of the ```git log``` command and returns it as a table.  Key to the success of this is figuring out how to run ```git log``` from inside python (there are multiple ways) and to make sure that your output data is formated in a way consistent with what is expected as input down stream. 

**_HINT_** You may want to consider working with Group 2 to find a common syntax for accessing git from python.

&#9989; **<font color=red>DO THIS:</font>** Identify or clone a git repository you can use for testing.  Pick one with lots of entries from a handful of authors. (Ex: [SEE-Segment](https://github.com/see-insight/see-segment))

&#9989; **<font color=red>DO THIS:</font>** As a group, create a file called ```group1.py``` and write a function called ```git_log``` that takes in a path to a git folder (default current folder '.') and uses the "git log" command to generate a table of git commits from the folder and includes the following fields: Author, Date, Hash, Comment. Output this as a pandas table. As you make changes, commit/push this file to the assignment git repository. 


----
<a name="S2"></a>
## Group 2: Measure the magnitude of a contribution (```diff```)

```python
nlines = git_diff(hash1, hash2)
```

This group's job is to write a function that takes two repository "hashes" and parses the output of the ```git diff``` command to return an integer representing the number of lines changed between the two hashes.  Key to the success of this is figuring out how to run ```git diff``` from inside python (there are multiple ways) and to make sure that your output data is formated in a way consistent with what is expected as input down stream. 

**_HINT_** You may want to consider working with Group 1 to find a common syntax for accessing git from python.


&#9989; **<font color=red>DO THIS:</font>** Identify or clone a git repository you can use for testing.  Pick one with lots of entries from a handful of authors. (Ex: [SEE-Segment](https://github.com/see-insight/see-segment))

&#9989; **<font color=red>DO THIS:</font>** As a group, create a file called ```group2.py``` and write a function called ```git_diff``` that takes two hash values and parses the output of the "git diff" command to return an integer with the total number of lines made during that commit. As you make changes, commit/push this file to the assignment git repository. 

----
<a name="S3"></a>
## Group 3: Summarize the contribution of each author (```grade```)

```
authors = git_grade(author_table) 
```

This group's job is to write a function that takes a pandas table as input and uses the ```git_diff``` function to generate a dictionary of authors and the total number of lines that they have contributed.  Key to the success of this is figuring out how to write the loop without a working ```git_log``` or ```git_diff``` function.  this will require coordinating with group1 and group2 to make sure you get the syntax right.  

&#9989; **<font color=red>DO THIS:</font>** As a group, create a file called ```group3.py``` and write a function called ```git_grade``` which takes a pandas table as input and uses the Group 2 ```git_diff``` function to loop over all of the authors and adds up the total number of lines they contribute. This function should return a dictionary with tag for author names and values of their number of total lines. As you make changes, commit/push this file to the assignment git repository. 

----
<a name="S4"></a>
## Group 4 : Graph the results suitable to inform a grade decision (```graph```)

```
git_graph(authors)
```

This group's job is to write a function that takes a dictionary as input and outputs a graph representing the mangitude of contribution of authors for an input git repository. Key to the success of this is figuring out how best summarize and visualize the data in a way that is easy to understand by an instructor.  

&#9989; **<font color=red>DO THIS:</font>** As a group create a file called ```group4.py``` and write a function called ```git_graph``` which takes a dictionary of authors as inputs and generates a figure that clearly shows the contribution of each author and can be used to determine grading by an instructor.  As you make changes, commit/push this file to the assignment git repository. 


----
<a name="S5"></a>
## Group 5 : Management Group

The management group will create the team zoom room and a git repository and share it with the class. It is their job to organize the functions together and help support and coordinate the other groups. 



&#9989; **<font color=red>DO THIS:</font>** Have all of your members read though this entire document to see how your part of the project will fit in with other parts of the project. 



&#9989; **<font color=red>DO THIS:</font>** Create a git repository on [gitlab.msu.edu](http:\\gitlab.msu.edu\) and share this repository with all members of the class.  The file structure for your git repository should probably be something like the following:

```
-- git_grader_repository
 |-- .gitignore
 |-- README.md
 |-- group1.py
 |-- group2.py
 |-- group3.py
 |-- group4.py
 |-- git_grader_demo.ipynb
 |-- git_grade.py
```


&#9989; **<font color=red>DO THIS:</font>** Check in with each group and make sure they can clone and contribute to the repository their initial stub functions. 



&#9989; **<font color=red>DO THIS:</font>** Continue to review all groups code and make sure that everything will work together when it is all finished. Anticipate challenges, write test scripts, ask questions and provide help when needed.  Bring groups together for meetings if there is confusion.  Generally be there to help out and make sure the project has the resources it needs to succeed. 


&#9989; **<font color=red>DO THIS:</font>** Combine all of the functions into a single python file called ```git_grader.py```.  Create a jupyter notebook that demonstrates the use of the program on a couple of different git repositories.  **_DO NOT_** wait until the end to write these tests. Having them early will help you visualize what needs to be done. Something like the following:

```python
import git_grade as gg
author_table = gg.git_log() #Convert the output of "git log" command to a pandas table.


hash1 = author_table['Hash'][0]
hash2 = author_table['Hash'][1]
nlines = gg.diff(hash1, hash2)  # Show the number of lines for an individual hash contribution.

authors = gg.grade(author_table) # Generate a list of authors and their contribution for a repository.

gg.graph(authors) # Graph the results in a meaningful way. 
```

&#9989; **<font color=red>DO THIS:</font>** Coordinate a 5 minute (max) presentation and be ready to share what your entire team did with the instructor. Demos of the working code are expected. Be prepared to answer questions such as "what works?" "What doesn't work?" "is this a good way to grade contributions?", "describe something interesting or challenging that happened during the project" etc. (We will have presentations at the end of next Friday).

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
