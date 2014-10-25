def transformer (letter):
    return ord(letter)
print transformer ("a")


def stripSpaces(mystring):
    return mystring.replace(" ","")
    
    
    
    
def scramble (plaintext):
    even = ""
    odd = ""
    count = 0
    for ch in plaintext
        if count % 2 == 0:
            even = even + ch
        else:
            odd = odd + ch
        count = count + 1
    cypher = odd + even
    return cyper
    
    
    def keygen ():
    abc = qwew
    key = ""
    for i in range (len(abc)):
        ch = random.randint (0,25-i)
        key = key + abc (ch)
        abc = removeChar (abc, ch)
    return key
    
    
    
    removing duplicates
    def remove (myString):
    newstr = ""
    for ch in myString:
        if ch not in newstr:
        newstr = newstr + ch
    return newStr

remove the ch in one from another
def removematch (myS, remove )
news = ""
for ch in myS
    if ch not in remove:
        news = news + ch
return newStr
    
    
    
    def rot13(message):
    new_string = []    # This is our list
    for i in range(len(message)):
        if ord(message[i])>122 or ord(message[i])<97:   #here we make sure that the element is in the alphabet and not a comma or point or space
            new_string.append(message[i])		#if it’s outside our range, we leave it.
        else:
            new_char_value = ord(message[i]) + 13
            if new_char_value > 122:
                new_char_value -= 26	#if it goes beyond the value for z, we send it back 26 spaces, which will make it start from ‘a’ again
            new_string.append(chr(new_char_value))
    return ''.join(new_string)	#once we have all the characters modified, we join the list to an empty string to generate the new string.

    
    looking up a letter in the vignere square
    
    def fing (keylet, plaintext)
    keyInd = lettertoindex ( keylet)
    ptIndex = lettertoindex (plaintext)
    newInd = (ptIndex + keyInd) % 26
    return indextoLetter(newIdx)
    
    
    
    
    
    
    
    
    
    
    
    
    =VLOOKUP(lookup_value, table_array, col_index_num, range_lookup)

    
=1/(1+r)
CF equals face value * interest rate
Discount Factor for Each Year: =(1/(1+r))^year
Present Value: CF*DF
    
The price that someone who wants to hold the bill will pay for it at the time it is issued is the present value of that $10,000:
p = 10k/1+r

mortage
int paid=intrate*lent than intrate * remaining b
principal = total -int
remaining lent-princ / remaining-princ



Option Explicit

Sub ProfitsOverPrices()
'
' ProfitsOverPrices Macro
'
' Set up 21 iterations

Const n As Integer = 21
Dim i As Long

' This macro does not require a lot of programming, because the structure of the problem is built into the
' "Profit Max" worksheet. It is a long-run profit maximization problem, with all inputs variable.


' To run a macro that utilizes Solver, one must click on Tools... References... and make sure that the
' check box next to Solver is checked, then click OK. (This only needs to be done the first time one runs
' the macro, if one saves the workbook before closing it. These references can then be used in the future.)

' In order to have total control over how Solver will behave, it is best to reset it at the outset.

SOLVERReset

' It can be useful to set certain Solver options.  The maximum number of iterartions and the maximum
' amount of time allowed for the calculations can also be important, especially for complex optimization
' problems that involve many variables and that are repeated over and over, such as Monte Carlo simulations.
' We should allow enough time and iterations so that Solver does not pull up short of the solution.


' The more precision we request for our contraints ("Precision") and in convergence to a solution
' ("Convergence"), the longer the macro will take to run. This may be the difference between finishing
' a task in hours versus days or weeks!  See the information below on the various Solver options.

' Also notice how to continue of line in VBA, with the underscore character.

Solveroptions Precision:=0.00000001, StepThru:=False, Estimates:=1, Derivatives:=2, _
  Searchoption:=1, Scaling:=True, Convergence:=0.00000001, AssumeNonNeg:=True

' Make sure that the "Profit Max" worksheet is the active worksheet:

Sheets("Profit Max").Select

For i = 1 To n

' If we enter non-negativity constraints explicitly at slightly above zero, we want to reset Solver for each i,
' within the loop, to clear the prior constraints used.

'    SOLVERReset

'    Solveroptions Precision:=0.00000001, AssumeLinear:=False, StepThru:=False, Estimates:=1, Derivatives:=2, _
'        Searchoption:=1, IntTolerance:=5, Scaling:=True, Convergence:=0.0000000000001, AssumeNonNeg:=False

' Impose constraints that labor and capital be greater than or equal to (relation 3) 0.00001, to avoid
' wandering slightly into negative territory.

'    SolverAdd CellRef:=Cells(i + 1, 1), Relation:=3, FormulaText:="0.00001"
'    SolverAdd CellRef:=Cells(i + 1, 2), Relation:=3, FormulaText:="0.00001"


' The first argument in the Cells function is the desired row, the second is the desired column.

    SolverOk SetCell:=Cells(i + 1, 9), MaxMinVal:=1, ValueOf:="0", ByChange:= _
        Range(Cells(i + 1, 1), Cells(i + 1, 2))

' Note: If starting values are not very close to the solution, Solver may reach its convergence threshold
' before it reaches the solution. If this happens, rerunning Solver where it left off can do the trick.

' Automatically terminate each Solver run without prompting the user. The bad news is that it will be almost
' impossible for you to stop the macro from running once it starts, unless you force Excel to close, losing
' any data that have been changed.
    
    SolverSolve UserFinish:=True

Next i

'SolverOptions(MaxTime, Iterations, Precision, AssumeLinear, StepThru, Estimates, Derivatives, Search, IntTolerance, Scaling, Convergence, AssumeNonNeg)

'MaxTime   Optional Variant. The maximum amount of time (in seconds) Microsoft Excel will spend solving the problem. The value must be a positive integer.
'  The default value 100 is adequate for most small problems, but you can enter a value as high as 32,767.
'Iterations   Optional Variant. The maximum number of iterations Microsoft Excel will use in solving the problem. The value must be a positive integer.
'  The default value 100 is adequate for most small problems, but you can enter a value as high as 32,767.
'Precision   Optional Variant. A number between 0 (zero) and 1 that specifies the degree of precision to be used in solving the problem. The default precision
'  is 0.000001. A smaller number of decimal places (for example, 0.0001) indicates a lower degree of precision. In general, the higher the degree of precision
'  you specify (the smaller the number), the more time Solver will take to reach solutions.
'AssumeLinear   Optional Variant.True to have Solver assume that the underlying model is linear. This speeds the solution process, but it should be used only
'  if all the relationships in the model are linear. The default value is False.
'StepThru   Optional Variant.True to have Solver pause at each trial solution. You can pass Solver a macro to run at each pause by using the ShowRef argument of
'  the SolverSolve function. False to not have Solver pause at each trial solution. The default value is False.
'Estimates   Optional Variant. Specifies the approach used to obtain initial estimates of the basic variables in each one-dimensional search: 1 represents tangent
'  estimates, and 2 represents quadratic estimates. Tangent estimates use linear extrapolation from a tangent vector. Quadratic estimates use quadratic extrapolation;
'  this may improve the results for highly nonlinear problems. The default value is 1 (tangent estimates).
'Derivatives   Optional Variant. Specifies forward differencing or central differencing for estimates of partial derivatives of the objective and constraint
'  functions: 1 represents forward differencing, and 2 represents central differencing. Central differencing requires more worksheet recalculations, but it may
'  help with problems that generate a message saying that Solver could not improve the solution. With constraints whose values change rapidly near their limits,
'  you should use central differencing. The default value is 1 (forward differencing).
'Search   Optional Variant. Use the Search options to specify the search algorithm that will be used at each iteration to decide which direction to search in:
'  1 represents the Newton search method, and 2 represents the conjugate search method. Newton, which uses a quasi-Newton method, is the default search method.
'  This method typically requires more memory than the conjugate search method, but it requires fewer iterations. Conjugate gradient searching requires less memory
'  than the Newton search method, but it typically requires more iterations to reach a particular level of accuracy. You can try this method if you have a large
'  problem and memory usage is a concern. Conjugate searching is especially useful if stepping through the iterations reveals slow progress between successive
'  trial points.
'IntTolerance   Optional Variant. A decimal number between 0 (zero) and 1 that specifies the degree of integer tolerance. This argument applies only if integer
'  constraints have been defined. You can adjust the tolerance figure, which represents the percentage of error allowed in the optimal solution when an integer
'  constraint is used on any element of the problem. A higher degree of tolerance (allowable percentage of error) would tend to speed up the solution process.
'Scaling   Optional Variant. If two or more constraints differ by several orders of magnitude, True to have Solver scale the constraints to similar orders of
'  magnitude during computation. This is useful when the inputs (in the By Changing Cells box in the Solver Parameters dialog box) and outputs (in the Set Target
'  Cell and Subject to the Constraints boxes in the Solver Parameters dialog box) have large differences in magnitude — for example, maximizing percentage of profit
'  based on million-dollar investments. False to have Solver calculate without scaling the constraints. The default value is False.
'Convergence   Optional Variant. A number between 0 (zero) and 1 that specifies the degree of convergence tolerance for the nonlinear Solver. When the relative
'  change in the target cell value is less than this tolerance for the last five iterations, Solver stops and displays the message "Solver converged to the current
'  solution. All constraints are satisfied."
'AssumeNonNeg   Optional Variant.True to have Solver assume a lower limit of 0 (zero) for all adjustable (changing) cells that do not have explicit lower limits
'  in the Constraint list box (the cells must contain nonnegative values). False to have Solver use only the limits specified in the Constraint list box.

End Sub
With your mouse, drag the “Commodity Code” variable name into the “Row Labels” box below. Then drag the “Partner” variable into the “Column Labels” box below. Finally, drag the “Trade Value” variable into the “Values” box below.
