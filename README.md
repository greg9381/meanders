# meanders

This project was created as a tool to 1) quickly visualize some things related to math work that I'm doing, and 2) answer some questions I had about that work. [This paper](http://people.math.gatech.edu/~heitsch/Pubs/fpsac11.pdf) gives a detailed look at the topic, and skimming the first few pages (look at the pictures) is enough background to understand the code here. <br><br>
The two central classes in the project are PerfectMatching and Meander. A PerfectMatching (or "noncrossing perfect matching") is a line of 2n points, with arcs connecting points such that each point is connected to exactly one other point and none of the arcs intersect (either all arcs are drawn above the line for a particular matching, or all below). A meander is a pair of perfect matchings (with one matching's arcs drawn above the line and the other matching's arcs drawn below) where the arcs form a single closed loop. <br><br>
example of a noncrossing perfect matching: <br>
![](https://raw.githubusercontent.com/greg9381/meanders/master/graphics/matching.png) <br><br>
example of a meander: <br>
![](https://raw.githubusercontent.com/greg9381/meanders/master/graphics/meander.png)

# questions answered in this project

The first question was this: "Does there exist a meander such that for some 01 move on one of the matchings, no 01 move can be made on the other matching to return the meander to a single closed loop?" A perfect matching can also be represented as a string of 1's and 0's, with a 1 representing the beginning of an arc and a 0 representing the ending of one. For example:<br>
![](https://raw.githubusercontent.com/greg9381/meanders/master/graphics/01s_matching.png) <br><br>
A 01 move is an operation on a perfect matching in which an adjacent 1 and 0 are switched - this could be changing 01 to 10, or 10 to 01, but a 10 cannot always be changed to a 01 because these string representations have the property that any initial substring cannot contain more 0's than 1's (otherwise one of the later 0's would indicate the close of an arc in a place where all arcs up to that point are already closed), and switching a 10 to a 01 could upset this. For example, exchanging the fourth 1 in the above matching with the 0 following it results in this matching: ![](https://raw.githubusercontent.com/greg9381/meanders/master/graphics/01s_matching_after_move.png) <br><br>
The 01 move is a more restricted version of the "local move operation" described in the second section of the paper linked above. As shown in the paper, if a local move operation is performed on one of the matchings in a meander, then this will split the meander into two separate closed loops, but it is always possible to find a corresponding move on the other matching to "repair" the meander into a single loop again. I wanted to find out if the same could be said for 01 moves. More details can be found in Meander.java (testMatchings() method) and Catalan.java.

# more recent work

To help with the question of whether a graph of meanders of order *n* under pairs of 01 moves is connected, I created a way to draw the entire graph for a given *n*. The result for *n*=3 is shown below.<br>
![](https://raw.githubusercontent.com/greg9381/meanders/master/graphics/01moves_n=3.png)