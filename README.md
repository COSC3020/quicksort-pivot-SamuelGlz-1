[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/IF3rQO50)
# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Based on work from last semester:

For the median of three to pick a good pivot sort pivot we need the 
median of the begninning, middle and end of the list to be found in the middle range
of good pivots, as seen in slide 54 (lecture #1 sorting). (if the pivot is in the middle range it will split the list into two sublists with at least a ratio of $(\frac {1}{4})$ and $(\frac {3}{4})$ to get a run time of nlog_2 n).

Let:
G = an element that belongs in the middle range
S = an element that belongs in the lower range
B = an element that belongs in the upper range

The possibility of an element of a list to be part of the middle (G) range is ($\frac {1}{2}$)

And the possibility for an element of a list to be in the lower (S) or upper range(G) are both ($\frac {1}{4}$)

For the median to be G we need the elements to be 
-  At least 1 G, 1 S and 1 B, 
-  2 Gs and 1 of either S or B,
-  3 Gs,

So the P(GoodPivot) = P(P(1 G, 1 S and 1 B)  $\cup$ P(2 Gs and 1 of either S or B) $\cup$ P(3 Gs))

There are 27 ways we can order G, S and B in groups of three, we count the number of versions of each group like so

- At least 1 G, 1 S and 1 B, 3! = (3*2*1) = 6 ways 
- 2 Gs and 1 of either S or B, 3! = (3*2*1) = 6 ways 
- 3 Gs, there is only one version of this group

Now we can calculate the probability of picking 

- P(1 G, 1 S and 1 B) = 6 * $(\frac {1}{2}) * (\frac {1}{4}) * (\frac {1}{4}) = (\frac {1}{32})$ = $\frac{6}{32}$
- P(2 Gs and 1 of either S or B) = 6* $(\frac {1}{2}) * (\frac {1}{2})*(\frac {1}{4}) = (\frac {1}{16})$ = $\frac{6}{16}$
- P(3 Gs) = 1* $(\frac {1}{2})$ * $(\frac {1}{2})$ * $(\frac {1}{2})$ = $(\frac {1}{32})$ = $\frac{1}{8}$

So P(GoodPivot) = $\frac{1}{8} + \frac{6}{16} + \frac{6}{32} = \frac{11}{16} $

So we can say that if we use the median of three method to pick a pivot we will get a good pivot $\frac{11}{16} \asymp 68.7$% which is a better than the 50% at random (or the random number in the first position)