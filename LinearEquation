from fractions import Fraction
import decimal

def FindPivotElement(): # finding pivot element
    temp1 = 0 # temp1 holds position of the temp1
    temp = given[LR-1][0] # temp holds the smallest value of the last row
    for x in range(LC-1): # checking last row to find the smallest value of last row
        if given[LR-1][x+1] < temp: # if next element is smaller than previous,
            temp = given[LR-1][x+1] # temp holds the smallest value
            temp1 = x+1 # temp1 holds the position of smallest value

    # find if temp1 is negative
    if given[LR-1][temp1] >= 0: # if the last row does not have negative number, return 0
        return 0
    else: # if last row has negative number, we do ratio test
        ratio_test = [] # dynamic array for ratio test
        for x in range(LR-1): # find ratio test value for every row except last row
            if given[x][temp1] == 0:
                ratio_test.append(0)
            else:
                ratio_test.append(given[x][LC-1]/given[x][temp1]) # creating a ratio_test array
        temp2 = 0 # temp2 holds pivot row position (smallest value of ratio_test array)
        temp3 = ratio_test[0] # temp3 holds the smallest value of ratio_test array
        for x in range(len(ratio_test)-1): # finding which row is pivot row (smallest value of ratio_test)
            if temp3 <= 0: # if the value is negative number, we assign temp3 to next value because we are looking for non-negative number
                temp3 = ratio_test[x+1]
                temp2 = x+1
            elif ratio_test[x+1] < temp3 and ratio_test[x+1] > 0: # if the next item is smaller than present value AND the next item is NOT negative
                temp3 = ratio_test[x+1] # temp3 now holds the smallest value
                temp2 = x+1
        #temp1 = pivot column, temp2 = pivot row
    return temp1, temp2

def Normalize(x,y):
    temp = given[y][x] # holds pivot element value
    for i in range(LC): # dividing every items in the pivot row by pivot element
            given[y][i] = given[y][i]/temp
    print(given)
    return given

def Iterate(x,y): # iterate every row
    for i in range(LR): # all row
        if i != y: # do not iterate the pivot row
            temp1 = given[i][x] # temp1 holds the value in pivot column of the first
            if temp1 == 0:
                pass
            else:
                for j in range(LC):
                    given[y][j] = temp1*given[y][j]
                    given[i][j] = given[i][j] - given[y][j]
                    given[y][j] = given[y][j]/temp1
    print(given)
    return given




#given = [[1,2,1,0,40],[4,3,0,1,120],[-40,-50,0,0,0]] # example matrix
given = [[-1,1,1,0,0,11],[1,1,0,1,0,27],[2,5,0,0,1,90],[-4,-6,0,0,0,0]]
#given = [[2,1,0,1,0,0,10],[1,2,-2,0,1,0,20],[0,1,2,0,0,1,5],[-2,1,-2,0,0,0,0]]
LR = len(given)
LC = len(given[0])
N = 3 # number of variables

while FindPivotElement() != 0:
    x,y = FindPivotElement() # x = pivot column, y = pivot row
    print(x,y)
    Normalize(x,y)
    Iterate(x,y)

for x in range(LR):
    given[x][LC-1] = round(given[x][LC-1],2)

print(given)

for x in range(LR-1):
    for y in range(N):
        if given[x][y] == 1:
            print('x', x+1 ,' = ', given[x][LC-1])
            break
    else:
        print('x', x+1, ' = ', 0)

print('Maximized profit: ', given[LR-1][LC-1])
