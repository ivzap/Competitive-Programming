## `Problem Link:`https://www.hackerrank.com/challenges/grading/problem
Pretty straight forward solution, for each grade in the input list, the code does the following:
- If the grade is less than 38, it does nothing and moves on to the next grade.
- If the grade is 38 or above, it checks if the grade is less than 3 away from the next multiple of 5. If it is, the code does nothing and moves on to the next grade.
- If the grade is more than 2 away from the next multiple of 5, the code rounds the grade up to the next multiple of 5 and updates the grade in the input list.

For example, if the input list is `[73, 67, 38, 33]`, the function will modify the list to be `[75, 67, 40, 33]` before returning it.
![image](https://user-images.githubusercontent.com/64557487/211226061-fc022e16-63ab-40d2-a0ca-8f9c0db81d74.png)


## Difficulty: `Easy`

```python
def gradingStudents(grades):
    for i, grade in enumerate(grades):
        if grade < 38:
            continue
        elif grade % 5 >= 3:
            grades[i] = (grade // 5 + 1) * 5
    return grades
```
