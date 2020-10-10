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


n = storys
f = floors
e = eggs

E(e, f):
  create a 2d table first of floors by eggs.
  eggFloor = [[0 for x in range(f + 1)]for x in range(e + 1)]

  start filling base cases
  for i in range(1, e + 1):
    eggFloor[i][1]=1
    eggFloor[i][0]=0
  fill one egg trials
  for j in range(1, f + 1):
    eggFloor[1][j] = j
  fill rest of entries in table.
  for i in range(2, e + 1):  for every egg
    for j in range(2, f + 1): for every floor
      for x in range(1, j + 1): run a trial
                      if a egg breaks it has to be a lesser floor
                      if it doesnt it has to be a upper floor
        res = 1 + max(eggFloor[i-1][x-1], eggFloor[i][j-x]) which is higher the egg breaking or not breaking

        if res < eggFloor[i][j]:
          eggFloor[i][j] = res
  return eggFloor[e][f]

  time complexity of O(e\*f^2)so O(n*k^2)