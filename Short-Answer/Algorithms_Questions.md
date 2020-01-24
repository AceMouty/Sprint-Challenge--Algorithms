# Analysis of Algorithms

## Exercise I

Give an analysis of the running time of each snippet of
pseudocode with respect to the input size n of each of the following:

```python
a)  a = 0
    while (a < n * n * n):
      a = a + n * n
```


```
b)  sum = 0
    for i in range(n):
      j = 1
      while j < n:
        j *= 2
        sum += 1
```

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```

## Exercise II

Suppose that you have an n-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor f or higher, and doesn't get broken if dropped off a floor less than floor f. Devise a strategy to determine the value of f such that the number of dropped + broken eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode AND give the runtime complexity of your solution.


instinct is to drop an egg from every floor and check if the egg is broken or not, if it doesnt break move up to the next floor and repeat. This is a linear
approach to the problem but does not balance the number of eggs dropped vs the eggs broken.
Time complexity of this would be O(n)

First thought / idae:
n = 6
will drop an egg starting from floor f if it breaks then we can only drop from floor f - 1
if not move up to floor current floor = f + 1 and drop

6            6            6
5            5            5
4            4            4
3      =>    3    =>      3
2            2            2 < floor
1            1 < floor    1
0 < floor    0            0


The second idea that comes to mind is a Binary search. Find the range of floors select the middle floor and drop an egg.
if the egg breaks we are to high and need to choose a floor that is half way down from the current floor that we are on drop again rinse and repeat.
however if it doesnt break, choose a floor that is half way up from the remaing floors higher than the current floor we are on, rinse and repeat.

The time complexity of the binary search would be O(log n) since we are dividing our options through each itteration (cutting them in half) until we find our
answer this will also minimize the number of drops that we have and the number of breaks we have.


6             6            6
5             5 < floor    5
4             4            4 < floor
3 < floor =>  3    =>      3
2             2            2 
1             1            1
0             0            0
