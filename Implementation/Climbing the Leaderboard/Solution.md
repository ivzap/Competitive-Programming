## `Problem Link:` https://www.hackerrank.com/challenges/climbing-the-leaderboard/problem

`binary_search()` takes in a target value and a sorted list `board`and returns the index of the target value in the list if it is present, or the index where it should be inserted to preserve the sorted order of the list if it is not present. It does this using a modified binary search algorithm, which repeatedly splits the list in half until the target value is found or it is clear that the target value is not present in the list.

`climbingLeaderboard()` takes in two lists: ranked, a list of integers representing the scores of the players in a game ranked from highest to lowest, and player, a list of integers representing the scores of a single player in a series of games. It returns a list of integers representing the ranking of the player after each game, with the first element representing the ranking after the first game, the second element representing the ranking after the second game, and so on.

To do this, `climbingLeaderboard()` first initializes an empty list `ranks` and a list `results` to store the rankings of the player after each game. It then loops through the elements of ranked and generates a list `ranks` such that `ranks[i]` is the ranking of the player with score `ranked[i]`. It does this by assigning `ranks[0]` a value of 1 and then, for each subsequent element `ranked[i]`, if `ranked[i]` is the same as the previous element `ranked[i-1]`, it assigns `ranks[i]` the same value as `ranks[i-1]`, otherwise it assigns `ranks[i]` a value of `ranks[i-1] + 1`.

Then it loops through the elements of player and, for each score score, it checks three conditions:

- If score is greater than the highest score in `ranked`, it appends 1 to `results` (since the player would have the highest ranking in this case).
- If score is less than the lowest score in `ranked`, it appends the last element of `ranks` plus 1 to `results` (since the player would have a ranking one greater than the lowest ranking in this case).
- If score is neither the highest nor the lowest, it calls `binary_search()` to find the index of the last element in ranked that is less than or equal to score and appends the corresponding element of ranks to results.

Finally, it returns `results`.

## Difficulty: `Medium`


```python
def binary_search(target, board):
    left = 0
    right = len(board) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if board[mid] == target:
            return mid
        elif board[mid] < target < board[mid-1]:
            return mid
        elif board[mid] > target >= board[mid+1]:
            return mid + 1
        elif target > board[mid]:
            right = mid - 1
        elif target < board[mid]:
            left = mid + 1
    return -1

def climbingLeaderboard(ranked, player):
    ranks = [1]
    results = []
    for i in range(1, len(ranked)):
        if ranked[i-1] == ranked[i]:
            ranks.append(ranks[i-1])
        else:
            ranks.append(ranks[i-1] + 1)
    for score in player:
        if score > ranked[0]:
            results.append(1)
        elif score < ranked[-1]:
            results.append(ranks[-1] + 1)
        else:
            index = binary_search(score, ranked)
            results.append(ranks[index])
    return results
```
