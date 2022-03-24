# In-Class Assignment: Graph Coloring 

**NOTE:** I am planning on having this assignment take two class periods. That is fine, lets take our time so we can learn something.

In class today we are going to try an experiment to write some code as a team.  We will take a fairly complex problem and divide it up into parts. Each person or sub-groups of people will work on their part and then we will try to compile them as a group and see if they all work together.  

### Project description

The signals from different cellphone towers that are close together can interfere.  

<img src="http://2.bp.blogspot.com/-X7XJfnPb6xU/TjZfTmAd9CI/AAAAAAAAAF0/3eGarXigOQE/s1600/dido1.jpg" width="50%"><p style="text-align: right;">From: http://www.onlivespot.com/2011/08/dido-wireless-technology-explained.html</p>

In order to avoid this overlap cell phone companies use different frequency ranges in the Electromagnetic spectrum.  Two towers that are close together but have differences in frequencies (shown as colors, red/green/black in the following figure) do not cause nearly as much interference. 

<img src="http://2.bp.blogspot.com/-M4olRy6O-v4/TjZghvwq3KI/AAAAAAAAAF4/GtOd6Db-su4/s1600/dido2.jpg" width = "50%"><p style="text-align: right;">From:  http://www.onlivespot.com/2011/08/dido-wireless-technology-explained.html</p>

However, cellphone towers are never distributed in such an even pattern.   Consider the following map which shows the location of cell towers around Michigan State.

<img src='https://lh6.googleusercontent.com/qSPlrmlnBqN7JZu_U_zaOydbFhekPtQhYk2s0fmMo__5YktgYXWuenVkKATZ0uaDNfrex51kUW8SseGjFMMcL8yYPcuMc3_o5H125HMzvI1wd91ZM8XV98tLx23-=w740' width = "50%">

From: [http://www.antennasearch.com/](http://www.antennasearch.com/)

Another problem is that cellphone companies have to pay for each frequency range they use.  So they would like minimize the number of frequencies that they need to purchase while also minimizing the interference between the cell towers. 

Today we are going to go though the steps to solve this problem using graph theory.

### Agenda for today's class (80 minutes)

1. (10 minutes) Set up groups
2. [(70 minutes) Group Programming Project](#Group_programming_Project)

---

# 1. Setting up Groups

Use the following Google document to share notes with the other members of your team.

- [Google Document](https://docs.google.com/document/d/1BS_n0P-a_TenNtcEHU3mT6T2K5PGu4qFNi6YZb5MNqk/edit?usp=sharing)

|   | Team A | Team B|
|---|--------|-------|
| **_Download_** | Boeing | Ford |
| **_Knn_** |  Hope Village | AFRL|
| **_Graph Coloring_** | Argonne |  Neogen | 
| **_Map Plot_** | Old Nation | QSIDE | 
| **_Management_** | Kelloggs  | Delta Dental  |

----
<a name="Group_programming_Project"></a>
# 2. Group programming Project

I have broken the project down the following programming components:

1. [Download and import the data](#S1)
2. [Calculate k Nearest Neighbors](#S2)
3. [Greedy Graph Coloring](#S3)
4. [Plot tower colors on a map](#S4)
5. [Management Group](#S5)

Assuming we get all of these steps written as functions we could imagine a program of the following form

```
locations = downloadTowerData(filename)
graph = kNN(locations,k)
colors = GreedyGraphColoring(graph, M)
mapplot(locations, colors)
```

Where each of the variables are of the following types:

- ```locations``` - $n \times 2$ numpy array of longitude and latitude point locations. (Similar to what we did in the pre-class)
- ```graph``` - adjacency matrix represented as a matrix.
- ```colors``` - $n$ list of numbers representing colors.  Is just indexes in the range $0-M$ where $M$ is just the number of colors we need to assign. 

We are going to try to write each component separately and then assemble them as a class. 

&#9989; **<font color=red>DO THIS:</font>** As a class break up evenly into groups, one group for each of the four steps plus a "management" group.  

The management group will create a git repository and share it with the class. It is their job to organize the functions together while individual groups work on them.  I recommend having each group generate a python file for their function with the end goal of getting something like the following working:

```python
from downloadTowerData import downloadTowerData
from kNN import kNN
from GreedyGraphColoring import GreedyGraphColoring
from mapplot import mapplot

locations = downloadTowerData(filename)
graph = kNN(locations,k)
colors = GreedyGraphColoring(graph, M)
mapplot(locations, colors)

```

For the other groups you should do the following:

1. First, write a stub function for your part. A stub function provides the inputs and outputs in a format that can be tested by the other groups. We need to agree and share stub functions using the git repository. (this is probably as far as we will get today).  **_NOTE:_** Make sure you get this done first before writing your main program.  
2. After each step graph or plot the output to make sure it is in the expect form.  
3. Write some test functions that send different data into your function and make sure it works as expected.
4. Update your stub function with the final version in the git repository. 

Key to the success of this project is careful communication between the groups.  If a group gets done early and join the management group to help each other out. Good luck!


----
<a name="S1"></a>
## Group 1: Download and import the data


```
locations = downloadTowerData(filename)
```

We will be using antenna data from the following website:

http://www.antennasearch.com/

Download a csv file from the above website for all of the towers in a 4.0 Mile radius from the MSU engineering building (567 Wilson Road, East Landing, MI 58824). 

&#9989; **<font color=red>DO THIS:</font>** Write a ```importTowerData``` stub function that ignores the input and returns a random $n \times 2$ set of points where $n$ is the number of towers. 

&#9989; **<font color=red>DO THIS:</font>** Write a ```importTowerData``` function to load the file into Python and generate a list of latitude and longitude for the towers. Output the points as a $n \times 2$ where $n$ is the number of towers. 

----
<a name="S2"></a>
## Group 2: Calculate K-Nearest Neighbors


```
graph = kNN(locations,k)
```

&#9989; **<font color=red>DO THIS:</font>** Write a function that takes a set of points as an $n \times 2$ numpy matrix and returns a random graph in the form of a python dictionary.  Doesn't have to be complex just something that can be easily passed on to the graph coloring function. 


&#9989; **<font color=red>DO THIS:</font>** Write a function that takes a set of points as an $n \times 2$ numpy matrix and returns an adjacency graph (in the form of a python dictionary).  More information about the algorithm can be found here:

https://en.wikipedia.org/wiki/Nearest_neighbor_graph

Basically the algorithm loops though all of the points and finds the nearest neighbor to each point.  


NOTE: This is what was attempted in the pre-class assignment.  Focus on generating a nearest neighbor algorithm that generates a dictionary and use the stub function from the pre-class to test the graph.  

----
<a name="S3"></a>
## Group 3: Greedy Graph Coloring


```
colors = GreedyGraphColoring(graph, M)
```

&#9989; **<font color=red>DO THIS:</font>** Write a stub function that takes a dictionary as an input and assigns a random color to each point in the graph. The colors will be represented as list of numbered indexes  0−M.

&#9989; **<font color=red>DO THIS:</font>** Write a function that takes a dictionary as an input and applies the  greedy graph coloring algorithm on the network.  It is highly recommended that you find a library that has already implemented greedy graph coloring but you can write the algorithm if you want. Hint there is a lot of descriptions of greedy graph coloring on google.

HINT: If you use an external library, the hardest part of this algorithm may be data converting from a dictionary to whatever format the library uses.  If done right, it is possible that the function is just a bunch of lines of code.  

----
<a name="S4"></a>
## Group 4 : Plot tower colors on a map


```
mapplot(locations, colors)
```

&#9989; **<font color=red>DO THIS:</font>** Write a stub function that takes a graph (as a dictionary) and a list of color indexes (as a list) and plots them.  The stub function can just use a simple ```scatter``` plot.  

&#9989; **<font color=red>DO THIS:</font>** This one is a little tricky so extend the stub function to then color the plot using the color indexes.  Assign a unique color for each index.  We can assume a finite indexes of 4-5 colors but think about how the function should handle the case with a very large $M$. 

&#9989; **<font color=red>DO THIS:</font>** Write a function that takes a graph and a list of color indexes and plots them on a map of Michigan State. Similar to the following:

<img src="https://lh6.googleusercontent.com/qSPlrmlnBqN7JZu_U_zaOydbFhekPtQhYk2s0fmMo__5YktgYXWuenVkKATZ0uaDNfrex51kUW8SseGjFMMcL8yYPcuMc3_o5H125HMzvI1wd91ZM8XV98tLx23-=w740" width="33%">


Hint: I highly recommend using the [folium](https://python-visualization.github.io/folium) library. 

Written by Dr. Dirk Colbry, Michigan State University
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.
