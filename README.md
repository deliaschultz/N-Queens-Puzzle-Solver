#queens.py
def solve_queens(n): 

    perm_combinations = []
    for num in range(1, n + 1):
         perm_combinations.append(num)

    output = []
    # new_output = sorted(output)
    #check = True

    for solution in all_perms(perm_combinations):
        check = True
        for queen in range(len(solution) - 1):
            for opp in range(queen + 1, len(solution)):
                if abs(queen - opp) == abs(solution[queen] - solution[opp]):
                    check = False
                    break

        if check:
            output.append(solution)
            
    return sorted(output)

# make a generator
def all_perms(elements):
    if len(elements) <= 1:
        yield elements
    else:
        for perm in all_perms(elements[1:]):
            for i in range(len(elements)):
                yield perm[:i] + elements[0:1] + perm[i:] 



if __name__ == '__main__':
    n = int(input('Enter a number of queens: \n'))
    solutions = solve_queens(n)
    print(f'The {n}-queens puzzle has {len(solutions)} solutions:')
    for solution in solutions: 
        print (solution)
  
