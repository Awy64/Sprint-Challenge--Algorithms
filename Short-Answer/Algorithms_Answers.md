#### Please add your answers to the ***Analysis of  Algorithms*** exercises here.

## Exercise I

a)0(n)


b)0(n^2)


c)0(n)

## Exercise II

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
