SPRDist: Tool to compute exact subtree prune and regraft distance 

Version 1.0.2. 

**************************************************************************
* WHAT IS SPRDist?
**************************************************************************

SPRDist uses integer programming to solve the problem of computing
rSPR distances between two rooted binary trees. For introduction on
what is rSPR, you can google the web to find many pointers on this
subject.

Something you need to know before using the program: the trees are ROOTED 
and need to be binary. The running time varies. I have been able to solve
trees with 30 leaves or more for some data. If you have better ILP
solver (like CPLEX), that will speedup the program greatly. To use
CPLEX, you need to rebuild the program with CPLEX option (after
making changes to Makefile for the path of the CPLEX library). 
For this, you will need source code, which is available upon request.


**************************************************************************
HOW IT WORKS?
**************************************************************************

A fundemental result due to Semple, Steel and their co-authors is about
the link between maximum agreemen forest and SPR. In particular, it was
shown that by slightly modifying the two input trees, solving the maximum
agreement forest (MAF) problem gives solution to rSPR. The modification
is indeed simple: you only need to add a dummy leaf that is directly
connected to the root (this leaf is considered as a new species in the tree). 
And the rSPR distance is equal to the number of trees in a MAF minus one.

Not surprisingly, the MAF problem is NP-complete. While several authors
worked on approximation algorithms, my focus here is different: I want 
to compute rSPR exactly using ILP based on the MAF property. 

Recall that the MAF is to decompose the two trees into pieces, while
the pieces are exactly the same in two forests (one per input tree). 
The following simple formulation assumes the above modification on
the input trees are done (you do not need to do this to use the program,
because this program does that automatically for you). Obviously, the
key is ensure the subtrees in the forests are identical.
The basic observation is to rely on the triples of a rooted tree.
Refer to the manuscript "A Practical Method for Exact Computation 
of Subtree Prune and Regraft Distance". This will be available
once it is accepted for publication.


**************************************************************************
HOW TO PREPARE INPUT, RUN AND GET THE RESULTS??
**************************************************************************

The trees file contains two lines, one for each tree.
The trees should be in the popular Newick format.
A simple example is as follows:

(4,(3,(2,1)))
(2,(3,(1,4)))

The basic operation this program supports is to simply run:
./SPRDist -N <trees-file-name>

Alternatively, you can have two trees, each in a separate file.
For example, one file may contain 

(4,(3,(2,1)))

as it is only line, and the other file contains:

(2,(3,(1,4)))

Then you can use the command ine:
./SPRDist -T <tree1-file-name> <tree2-file-name>

There are a few other options currently in this version, 
but will no longer be supported.

The output says the rSPR distance between two trees, and it also
outputs a list of trees in a MAF. You can play around these
trees in the MAF to figure out a sequence on how to transform
one tree to another. 





