---
layout: post
title: Hill-climbing Algorithm!
---

Hill-climbing algorithm is part of a category of algorithm called local search.  These are optimization algorithms, ie 
finding the minimum or maximum of function. Sometimes it isn't possible to use differentiation
to find the minimum or maximum, some functions are not explicitly define and to be differentiable a function must be continuous, and
not all functions are continuous.

Local Search such as Hill-climbing are ideal if you can measure the result of a propose solution.  For instance,
you have 5 cities to travel. Each of the cities have a distance between them.  Your mission if you choose to accept it is
to try to minimize the distance travelled.  This problem is ideal for a local search algorithm, we are able to test the usefulness 
of a proposed solution, ie by measure the distance travelled by the order in which we try to travel the cities.   This is what we call
a travelling salesman problem;  there are number of problems similar to it.  The premise is to try an optimize a problem with a
combinatorial solution space.

Let's our 5 cities are: <br>
New York, St. John's, Paris, Perth, Nottingham.

The Distance between each city are as follows[made up data]:<br>
Point of Origin -> New York  = 300 mi<br>
New York -> St. John's = 300 mi<br>
New York -> Paris = 560 mi<br>
New York -> Perth =  830 mi<br>
New York -> Nottingham = 500 mi<br>

Point of Origin -> St. John's = 2 mi<br>
St. John's -> Paris = 350 mi<br>
St. John's -> Perth = 200 mi<br>
St. John's -> Nottingham = 320 mi<br>

Point of Origin -> Paris = 310 mi<br>
Paris -> Perth = 300 mi<br>
Paris -> Nottingham = 490 mi<br>

Point of Origin -> Perth = 190 mi<br>
Perth -> Nottingham = 220mi<br>

Point of Origin -> Nottingham = 330 mi

So, lets say we decided to use a greed algorithm to solve this, ie we select the shortest city from our current location.  The 
path we take is  Origin->St.John's->Perth->Nottingham->Paris->New York , total distance = 2 + 200 + 220 + 490 + 560 = 1472 mi. 
If you instead have chosen: Origin ->St.John's ->New York -> Nottingham -> Perth -> Paris = 2 + 300 + 500 + 220 + 300 = 1322 mi.
So, a greedy algorithm wouldn't necessarily work to be the optimum.  For these types of problem all possible combinations
would need to be generated and the one with the minimum distance chosen to be the resulting answer.  So, happens the problem
results in a combinatorial explosion of possible solutions.  For a problem, with 5 cities there are 5! possible solution but
when you have 100 cities that is 100! solutions, a huge number[go type it in on your calculator]. It would probably take us on the
order of the life time of the universe to be able to generate that many solutions; we can't wait that long.

So, what we need is a good enough solution, that is better than greed algorithm but gets to the results in a timely manner.  In comes, 
Hill Climbing algorithm.  Works by:<br>
0.  Initial our current solution to a random solution.<br>
1.  Alter the current solution a little bit.<br>
2.  Is altered solution better than our current solution, if yes our altered solution becomes our current solution else discard the altered solution.
3.  Repeat 1 and 2 until no change in solution after a number of tries of altered solutions.<br>
4.  Print current solution

You will notice that our solution to the problem keeps getting better.  For example, we travel a path randomly; if it is better than
any other previous part travelled we make that our current solution.   We keep doing that until the current solution doesn't change for
a significant number of iterations.

Code:<br>
{% gist chestergrant/1e75d79546da73a8ff7a %}

A executable version can be found <a href="http://codepad.org/db6Ov1UF" target="_blank">here</a>.

