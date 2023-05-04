Download Link: https://assignmentchef.com/product/solved-csci360-lab-2
<br>
. <strong>Problem Description</strong>: We have a stack of <em>n </em>textbooks that need to be sorted, such that the frontmatter of each textbook is facing up. For example, initially, we may have the following stack (<em>m</em>=7):

<h1>                                                                                                          1   0</h1>

<ul>

 <li>1</li>

 <li>1</li>

</ul>

7   0

3   1

<h1>                                                                                                          2   1</h1>

6   0

where the first number in each row shows the desired order of the textbook, and the second number shows whether the cover is frontmatter of the textbook is facing up (1) or facing down (0).

The goal is to sort the textbooks so that they form the following stack:

<ul>

 <li>1</li>

 <li>1</li>

</ul>

<h1>                                                                                                          3   1</h1>

4   1

<h1>                                                                                                          5   1</h1>

6   1

<h1>                                                                                                          7   1</h1>

However, to sort the stack, we are only allowed to select one of the textbooks, lift that textbook and all textbooks on top of it,<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> and flip them altogether. For example, assume that we select textbook 7 in the following stack:

1   0

<ul>

 <li>1</li>

 <li>1</li>

</ul>

2   1

<h1>                                                                                                          6   0</h1>

Flipping that textbook and everything above it will give us the following stack of textbooks:

7   1

5   0

4   0

1   1

3   1

2   1

6   0

We wish to start from an arbitrary stack, and do a finite number of flips and sort the textbooks.

<ol start="2">

 <li>The goal of this Lab is that you write a program that takes an initial stack of textbooks of size <em>n</em>, and sorts them using A* Search. A* uses a priority queue as its fringe. In order to implement the priority queue efficiently, you are recommended to use a binary heap. The cost function <em>g</em>(<em>n</em>) is the number of flips so far. The heuristic function that you will use is the number of pairs in the stack that satisfy one the following conditions:

  <ul>

   <li>If the pair of books are not adjacent in the ordered stack, regardless of being face up or face down.</li>

   <li>If the pair has a book facing up and one facing down.</li>

   <li>If the pair is wrongly ordered, but with correct orientations (both facing up)</li>

   <li>If the pair is correctly ordered, but with wrong orientations (both facing down) For example, in

    <ul>

     <li>1</li>

     <li>1</li>

     <li>1</li>

     <li>0</li>

     <li>0</li>

    </ul></li>

  </ul></li>

</ol>

7   1

<ul>

 <li>1</li>

 <li>1</li>

 <li>1</li>

</ul>

(6,8) is of the first type, (3,4) is of the second type,(opposite orientations), (7,6) is of the third type (correct orientations, wrong order), and (4,5) is of the fourth type (wrong orientations, correct order). There is also the pair (5,7) which falls in both the first and the second category. This pair is of course only counted once to maintain admissibility. (so, a pair is counted if it is of first, second, third, or fourth type, and this is LOGICAL OR). So, <em>h </em>= 5.

We have provided a skeleton code with extensive comments in the README.md file that you should read. Please use the skeleton code and submit your code to the GitHub repository that will be provided to you.

Here is how your code will be graded:

<ul>

 <li>General soundness of code: 60 pts.</li>

 <li>Passing multiple test cases: 40 pts.</li>

</ul>

<ol start="3">

 <li><strong>Extra Credit A* with Dynamic Weighting</strong>): One way of dealing with large state spaces is to use weighted A* algorithm, which uses:</li>

</ol>

<em>f</em>(<em>n</em>) = <em>g</em>(<em>n</em>) + <em>wh</em>(<em>n</em>)

Weighted A* uses the heuristic to find the goal faster, although it compromises optimality. If <em>w </em>= 0, it becomes Uniform Cost Search. If <em>w </em>= 1, it is the classic A* algorithm. The larger the <em>w</em>, the more it resembles greedy search. An idea to benefit from both the heuristic and the cost function is to use dynamic weighting, which uses a large weight at the beginning and uses greedy search to take us “somewhere” first, and then “fine-tuning ” using A*.

The weighted cost function is:

<em>d</em>(<em>n</em>) is the depth of the current search and <em>N </em>is an upper bound on the search depth (<em>N </em>≥ <em>d</em>(<em>n</em>)<em>,</em>∀<em>n</em>) . Implement the A* search with dynamic weight using <em> </em>= 1 and <em>N </em>= 2<em>m</em>, where <em>m </em>is the size of the stack of textbooks. Create a table and record the average number of flips needed for ordering over all permutations of textbooks when <em>m </em>∈{1<em>,</em>2<em>,…,</em>8} when you use A* and dynamically weighted A*.

<em>m      </em>A<sup>∗ </sup>Dynamically weighted A<sup>∗</sup>

1

2

3

4

5

6

7

<h1>8</h1>

Also, make a similar table about the average number of nodes visited. Provide your analysis based on those two tables. Submit a PDF file of both of the tables along with your code.

<a href="#_ftnref1" name="_ftn1">[1]</a> The top textbook has no textbook on top of it, so in case it is selected, it will be the only textbook that flips.