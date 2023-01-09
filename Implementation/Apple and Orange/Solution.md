## `Problem Link:` https://www.hackerrank.com/challenges/apple-and-orange/problem

The function calculates the number of apples and oranges that landed on the roof of the house and prints the results.

The code first defines two variables, `apple_location` and `orange_location`, to represent the distances of the apple tree and orange tree from the house, respectively. It then creates a range object representing the range of points on the house using the start and end points `s` and `t`.

The code then initializes two variables, `landed_apples` and `landed_oranges`, to 0. It then uses a for loop to iterate over the `apples` list. For each apple in the list, it checks whether the distance from the house to the apple (represented by apple + a) is within the range of points on the house. If it is, the code increments the `landed_apples` variable by 1.

![image](https://user-images.githubusercontent.com/64557487/211226395-f75583a7-aa0c-4f02-87c8-9bab9fa0fb78.png)


The code then does the same thing for the `oranges` list, using a for loop to iterate over the list and checking whether the distance from the house to each orange (represented by orange + b) is within the range of points on the house. If it is, the code increments the `landed_oranges` variable by 1.

## Difficulty: `Easy`

```python
def countApplesAndOranges(s, t, a, b, apples, oranges):
    apple_location = a
    orange_location = b

    house = range(s,t+1)

    landed_oranges = 0
    landed_apples = 0
    # find landed apples
    for apple in apples:
        if apple + a in house:
            landed_apples +=1
    # find landed oranges
    for orange in oranges:
        if orange + b  in house:
            landed_oranges +=1
            
    print(landed_apples)        
    print(landed_oranges)
```
