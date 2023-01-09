

```python
canidates = []

def make_canidates(canidate):
    if len(canidate) == 9:
        canidate = [ canidate[i:i+3] for i in range(0, 6+1,3)]
        magic_number = sum(canidate[0])
        if valid_canidate(canidate, magic_number):
            canidates.append(canidate)
        return
    for v in range(1, 9+1):
        if v not in canidate:
            canidate.append(v)
            make_canidates(canidate)
            canidate.remove(v)

def valid_rows(canidate, magic_number):
    for r in range(3):
        # test row, col, then diags
        if sum(canidate[r]) != magic_number:
            return False
    return True            
    
def valid_cols(canidate, magic_number):
    for c in range(3):
        if canidate[0][c] + canidate[1][c] + canidate[2][c] != magic_number:
            return False
    return True

def valid_diags(canidate, magic_number):
    diag1 = canidate[0][0] + canidate[1][1] + canidate[2][2]
    diag2 = canidate[0][2] + canidate[1][1] + canidate[2][0]
    return diag1 == magic_number and diag2 == magic_number

def valid_canidate(canidate, magic_number):
    return valid_rows(canidate, magic_number) and valid_cols(canidate, magic_number) and valid_diags(canidate, magic_number)
    
def formingMagicSquare(s):
    min_cost = sys.maxsize
    # make all possible magic square canidates
    make_canidates([])
    # filter canidates to only ones that are themselves a magic square
    for cand in canidates:
        cost = 0
        # calculate cost of conversion
        for r in range(3):
            for c in range(3):
                cost += abs(s[r][c] - cand[r][c])
        min_cost = min(min_cost, cost)
    # after all canidates have been converted to all canidates with their associated cost min_cost is correct
    return min_cost
```
