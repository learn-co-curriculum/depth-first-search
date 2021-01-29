## Depth First Search

There are multiple techniques for exploring the connectivity of a graph. In this lesson, we will discuss **depth first search** as one of these techniques.

### Depth First Search

Depth first search is one mechanism for determining if a graph is **connected**. Depth first search occurs similarly to how a child may explore a corn maze. Upon reaching a certain distance, just push on further until you hit a dead end. In other words, dive down one path, then dive down another path until all of the paths are explored.

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/Maize_kids-in-corn-slider.jpg)

### Our approach

Let's use our map of subway stops. Here we have a graph representing portions of the Sixth avenue line, the Broadway line, and the Lexington line.

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/graphedstops.png)

With depth first search, we start at a given vertex and _explore_ that vertex by visiting each of the adjacent vertices. Every time we visit a vertex we place it on a _stack_ (whatever that is), and the next vertex we explore is the top of the stack. This results in us visiting and exploring one line fully, like the 6th avenue line, and then backtracking to explore the Broadway and Lexington lines. Let's see how.

We randomly decide to start by visiting from 34th & 6th. Now that we visit the vertex, we place it on the top of the stack.

> Note: The way that a stack operates is _last in first out_ such that the last element inserted in is the first element removed from a stack. For example, think of stacking cafeteria trays on a trashcan: the last one in is on top, and therefore removed first.

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/trays-stack.jpg)

| stack      |
| ---------- |
| 34th & 6th |

We remove 34th & 6th from our stack, and explore the vertex by visiting all of the adjacent vertices. 34th and 6th has two adjacent vertices, 28th and Broadway and 23rd and 6th.

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/explored34.png)

So now take a look at our stack of visited vertices listed in the diagram above. It has 23rd and 6th and 28th and Broadway. We take the vertex from the top of the stack, 23rd & 6th, and explore that vertex. This means we look for adjacent unvisited nodes and find one in 14th & 6th. We add 14th and 6th to the top of the stack and will explore that next.

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/23rdexplored.png)

Ok, so now from the top of the stack, we choose 14th & 6th. From 14th & 6th there are no unvisited adjacent nodes, so we remove 14th and 6th from top of the stack, and will explore the next vertex on our stack at at 28th & Broadway. Note that this brings to explore the second path down from our root node.

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/exploring28.png)

From here, you may be able to fill in the rest of the procedure. We continue to explore the vertex at the top of our stack, which leads us to visit another node. And then we explore the next vertex at the top of our stack. We continue to do this we run out of vertexes to visit, at which point our stack will become empty and the algorithm will terminate.

Let's quickly go through these final steps.

Now that our stack looks like the following:

| top of stack    |
| --------------- |
| 28th & Broadway |

We remove 28th & Broadway from the top of the stack, and move onto 23rd & Broadway as it is the next adjacent unvisited node.

| top of stack    |
| --------------- |
| 23rd & Broadway |

From 23rd and Broadway our next unvisited adjacent node is 14th & Lex. We add that to the top of the stack.

| top of stack |
| ------------ |
| 14th & Lex   |

We remove 14th & Lex from the top of the stack, explore it, and find 23rd and Lex.

| top of stack |
| ------------ |
| 23rd & Lex   |

We remove 23rd and Lex, explore it only to find that there are no adjacent unvisited nodes, and so we terminate the algorithm.

### Summary

How would you summarize this procedure? How would you translate it into code? We'll ask you to translate this into code, so take a good look.
