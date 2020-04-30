# SPRDist
Software tool for computing distance between phylogenetic trees

Software accompaniment to
Yufeng Wu, A practical method for exact computation of subtree prune and regraft distance, Bioinformatics, v.25, pp. 190-196, 2009.

SPRDist is a program that takes two binary phylogenetic trees and computes the smallest number of subtree-prune-and-regraft (SPR) operations that transfrom one tree to the other. See the above figure for a very simple example of SPR. Note that when two trees are large and different, it is not easy to find the optimal SPR operations for the two trees. And that is the problem SPRDist is designed to solve.

Current version: v. 1.0.2. Source code is inclucded. You will need GLPK library to build. 

Input format: a very simple example input containing two trees, one per line (use -N option). Note that you can use -T option if you have two files, each containing a single line for a tree. Each tree is specified using the Newick format. For example,

((1,2),(3,4))
((1,3),(2,4))

Note: each taxa must be specified using numerical taxa, starting from 1 consecutively.
