## `Problem Link:` https://www.hackerrank.com/challenges/service-lane/problem

If you consider the constraints given, the solution to this problem becomes clear. A naive coder (like myself) might initially think that the problem requires `1,000 * 100,000` operations to be performed using an `O(t * n)` algorithm. However, the constraint that the number of elements in any slice of the road will be at most `min(n, 1000)` means that we only need to perform `1000 * 1000` operations per the constraint. Which is reasonable for a easy/O(n^2) algorithm. Simply create a brute force solution to solve this. That is, for every case, take the `min(widths[i:j])` as the max car width of that piece of the service road.

![image](https://user-images.githubusercontent.com/64557487/211416429-320d1413-1b65-4d7c-9d2f-4b46e1c51dc7.png)


Overall, this problem is a good one to practice your reading skills, how tiny details can sway your chances of solving or understanding the problem. Just read everything carefully.

## Difficulty: `Easy`
```python
def serviceLane(n, cases):
    max_widths = []
    for i, j in cases:
        temp_widths = width[i:j+1]
        if temp_widths:
            max_widths.append(min(temp_widths))
    return max_widths
```
