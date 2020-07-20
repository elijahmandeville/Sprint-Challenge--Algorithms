# Analysis of Algorithms

## Exercise I

Give an analysis of the running time of each snippet of
pseudocode with respect to the input size n of each of the following:

```python
a)  a = 0 # This would be O(1)
    while (a < n * n * n): # here it would be O(n3)
      a = a + n * n # This would be O(n2)
```

Since the input is a fixed value and it scales linearly with n, this is a linear runtime. After dropping all of the constants, it evens out to just O(n). In other words, the opperations are the same regardless of the value of n.

```python
b)  sum = 0
    for i in range(n):
      j = 1
      while j < n:
        j *= 2
        sum += 1
```

The instance of a nested loop would indicate a quadratic runtime. Each loop is dependent on n so you perform n \* n assignments meaning O(n^2) runtime. However, this could resemble a logarithmic runtime because j is doulbed each time.

```python
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```

Well if bunnies is 0 right off the bat, this is a constant runtime. Beyond that, this would be a linear runtime because the function scales linearly with bunnies since we are subtracting 1 from bunnies each time and then calling the function again. In other words, this is O(n).

## Exercise II

Suppose that you have an n-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor f or higher, and doesn't get broken if dropped off a floor less than floor f. Devise a strategy to determine the value of f such that the number of dropped + broken eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode AND give the runtime complexity of your solution.

I would start by cutting n in half and dropping an egg off the middle floor. If the egg breaks, I know that everything above the middle floor is irrelevant. I can take the left half, cut that in half, if it does NOT break on the middle of the left half, I know that I can move up a floor till egg == broken in which case the current_floor - 1 would be the max floor I could drop an egg.

If that first egg doesn't break, I can take the right half and do the same thing.

Because of the constant dividing of floor lengths, this would be a logarithmic runtime.
