## ` Problem Link:` https://www.hackerrank.com/challenges/matrix-rotation-algo/problem


To efficiently rotate the matrix, it is important to note that we only need to make `m` moves, where `m` is equal to the remainder of `r` divided by `d`. `r` represents the total number of rotations, while `d` represents the number of elements at the outermost depth of the matrix. This can be written as `m = r % d`

By performing `m` moves, we can achieve the desired rotation without performing exactly `r` operations which would TLE. I suggest practicing performing an arbitrary number of operations and then using the modulus to check that you arrive at the same solution. This will help you build confidence in your understanding of the concept. You may find it helpful to refer to the image as you practice.

![image](https://user-images.githubusercontent.com/64557487/211225443-7f8a9efd-b701-4510-a922-2165d33262ee.png)

The rest is just implementing the rotate function. Overall good problem to practice implementation skills.

## Difficulty: `Hard`




```python
def displayMatrix(matrix):
    for row in matrix:
        for num in row:
            print(num, end=" ")
        print()

def rotate(matrix, d):
    # down
    leftover = matrix[0+d][0+d]
    for i in range(1+d, m-d):
        temp = matrix[i][d]
        matrix[i][d] = leftover
        leftover = temp
    # right
    for i in range(1+d, n-d):
        temp = matrix[m-1-d][i]
        matrix[m-1-d][i] = leftover
        leftover = temp
    # up
    for i in range(m-2-d, -1+d, -1):
        temp = matrix[i][n-1-d]
        matrix[i][n-1-d] = leftover
        leftover = temp
    # left
    for i in range(n-2-d, -1+d, -1):
        temp = matrix[d][i]
        matrix[d][i] = leftover
        leftover = temp
    
def matrixRotation(matrix, r):
    M,N = m,n
    depth = 0    
    # keep rotating depths until none possibly remain
    while M > 1 and N > 1:
        moves = r % ((M*2 + N*2) - 4)
        # rotate the matrix at depth
        for _ in range(moves):
            rotate(matrix, depth)
        M-=2
        N-=2
        depth += 1
        
    displayMatrix(matrix)

```
