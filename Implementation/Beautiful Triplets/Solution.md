## `Problem Link:` https://www.hackerrank.com/challenges/beautiful-triplets/problem

While not evident at first, all we need is a bit of basic Combinatorics, and a Hashmap. It is important to consider that the problem only asks for the `number of triplets` which, if you are the seasoned competative programmer, screams some kind of mathematical 'trick'. 

Such trick is found by realizing:
- The sequence is in ascending order
- Knowing the value of d(given)

In an effort to make this intuitive, consider the following example...

```python

let d = 3
_        _        _
1  2  3  4  5  6  7  8

4-1 = 3
7-4 = 3
...

```
In a perfect sequence, that increases by 1 in each element, we simply maintain a sliding window of three elements that are `d` indices apart, to get a triplet with the differences of `d`.
Unfortunately we dont have perfect sequences like this for our problem, many elements are missing at times. To adjust, simply just find where that next element would be resulting in a element difference of `d`. 

The algorithm goes as follows:
- Find freq of all numbers in sequence
- Iterate over unique list of numbers
  - see if we have the element that will create a difference of `d`
  - check if we have a third element that will create a difference of `d` with the latter found element.
  - if the above passed, multiply freq of all numbers together to get all the possible combinations of such triplet(s).
- return the triplet counts





## Difficulty: `Easy`


  ```python
def beautifulTriplets(d, arr):
    count = 0
    sequence = Counter(arr)
    for x in sequence:
        if x + d in sequence and x+d*2 in sequence:
            count += sequence[x]*sequence[x+d]*sequence[x+d*2]
    return count
```
