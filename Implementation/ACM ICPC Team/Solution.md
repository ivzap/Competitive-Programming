## `Problem Link:` https://www.hackerrank.com/challenges/acm-icpc-team/problem
This problem is actually easier than I thought it was initially. 
We must solve `2 problems`:
- `Finding the max subjects within one team`
- `Finding the max amount of different ways we can form such group` (this was confusing, I thought it was the number of different groups that can be formed to make the max subjects found).

Simply iterate over each combination possible with two for loops, while keeping track of the number of subjects the group has. Reset the number of groups that can be formed when we change our max subjects found.

## Difficulty: `Easy`
```python
def acmTeam(topic):
    max_subjects = 0
    groups = 0
    for s1 in range(n):
        for s2 in range(s1+1,n):
            group_subjects = 0
            # count how many known subjects exist within group
            for s2_subj, s1_subj in zip(topic[s2], topic[s1]):
                if s2_subj == '1' or s1_subj == '1':
                    group_subjects += 1
            # update max subject and groups that can be formed with this subject count
            if group_subjects > max_subjects:
                max_subjects = group_subjects
                groups = 1
            elif group_subjects == max_subjects:
                groups += 1
    
    return [max_subjects, groups]
            
```
