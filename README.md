The purpose of histograms is to display absolute or relative frequencies for a single variable. In general, the command is

histogram varname, percent title( )


histogram testscr, percent title(Testscores)

scatter varname1 varname2

line str school
					twoway connected str school


The first way to look for a relationship is to plot the observations of both variables. This can be done by generalizing the command twoway connected to include more than two variable names (one for the Y axis and one for the X axis). Try this here with

twoway connected str testscr school

The resulting graph is pretty uninformative, since test scores and student-teacher ratios are on a different scale. You can allow for two (or more) scales by entering the following command:

twoway (scatter str school, c(1) yaxis(1)) (scatter testscr school, c(1) yaxis(2))


To get an even better idea about the relationship, you can display a two-dimensional relationship in a scatterplot (see page 92 of your Stock and Watson (2011) textbook). Given our discussion above, you could simply use the command scatter testscr str. However, you may want to see what a fitted line through that scatter plot would look like, in which case you have to modify the command slightly:

scatter testscr str || lfit testscr str

reg Y X

where “reg” stands for least squares regression. For the current application, type 

reg testscr str, r

gen” (as in generate) command. For example, Chapter 8 of the Stock/Watson textbook introduces the polynomial regression model, logarithms, and interactions between variables. Let us reproduce Equations (8.2), (8.11), (8.18), and (8.37) here. The following commands generate the necessary variables :

gen avginc2=avginc^2
gen avginc3=avginc^3
gen lavginc=log(avginc)
gen ltestscr=log(testscr)
gen strpctel=str*el_pct



reg testscore str

Testscr(hat) = 689.9 - 2.28 x str

n = 420, R^2 = 0.051, S.E.R. = 18.6

dont interpret the intercept 

(percentage point)


5.1% in the variation in testscores is explained by my model

S.E.R.

percntile 


statistically significant 
SEQ how much the quafitiant change (from sample to sample)




reject the null
becomes statistically significant



T score >2 
statistically significant


reg
putting another variable means that it holds it constant, 



controlling or ability
you just trhow in variables
twin studies you controlled for ability


saving stata bach file

do file


HW
1, inetrcept
 1.082275
slope
0.60
40*52*0.6



















* question 1
reg ahe age
dis _b[_cons]
dis _b[age]
 
*question 2 
sca Bob =_b[_cons]+_b[age]*26
sca Alexis =_b[_cons]+_b[age]*30
dis Bob
dis Alexis

*question 4 
reg ahe if bachelor == 0
reg ahe if bachelor == 1

*question 6
reg ahe age bachelor female 
dis _b[age]

*question 8
sca Bob =_b[_cons]+_b[age]*26
sca Alexis =_b[_cons]+_b[age]*30+_b[bachelor]+_b[female]
dis Bob
dis Alexis

*question 10
graph twoway (lfit ahe age) (scatter ahe age)
graph rename Figure_1

*question 11
gen logahe = log(ahe)
reg logahe age female bachelor
sca ageincrease = _b[age]*26 - _b[age]*25
sca ageincthirty = _b[age]*34 - _b[age]*33
dis ageincrease
dis ageincthirty

*question 12
gen agesquare = age^2
gen logahetwo = log(ahe)
reg logahe age agesquare female bachelor 
sca ageincrease = _b[agesquare]*26 + _b[age]*26 - _b[agesquare]*25 - _b[age]*25
sca ageincthirty = _b[agesquare]*34 + _b[age]*34 - _b[agesquare]*33 - _b[age]*33
dis ageincrease
dis ageincthirty

clear 
exit



import turtle

maxHEIGHT = 0
maxAGE = 0

height = [75,74,74,74,74,64,66,66,67,67]
age = [83,64,63,56,67,85,79,67,90,80]

aList = list(zip(height, age))

def calcM(x,y):
    sumxy = 0
    sumxsquared = 0
    x = height
    y = age
    for i in range(len(y)):
        sumxy += y[i]*x[i]
        sumxsquared += x[i]**(2)
    n = len(y)

    xMean = sum(height)/len(height)
    yMean = sum(age)/len(age)

    nuem = (sumxy-(n*xMean*yMean))
    denom = (sumxsquared-(n*(xMean**(2))))

    m = neum/denom
    return m


if height > maxHEIGHT:
    maxHEIGHT = height
if age > maxAGE:
    maxAGE = age

t = turtle.Turtle()
screen = t.getscreen()
screen.setworldcoordinates(0,0,maxHEIGHT,maxAGE)

t.goto(0,0)
screen.tracer(5)

def plotRegression(qList,t):
        rList = dict(qList)

        M = calcM(x,y)

        t.up()
        for i in range(len(y)):
            t.goto(x[i],y[i])
            t.down()
            t.up()
            
plotRegression(aList,t)
screen.update()
screen.exitonclick()
















def makeDictionary(key, value):
    dict = {}
    for i in range(len(key)):
        dict[key[i]]=value[i]
    return dict
names =['joe' , 'tom' , 'barb' , 'sue' , 'sally']
scores = [10,23,13,18,12]
scoreDict = makeDictionary(names, scores)


print(scoreDict.get('barb'))

scoreDict['john'] = 19




scoreDict['sally'] = scoreDict['sally'] + 1


def mean(scoreDict):
    mean = sum(scores) / len(scores)
    return mean


del scoreDict['tom']




HW
def makeDictionary(key, value):
    dict = {}
    for i in range(len(key)):
        dict[key[i]]=value[i]
    return dict
names =['joe' , 'tom' , 'barb' , 'sue' , 'sally']
scores = [10,23,13,18,12]
scoreDict = makeDictionary(names, scores)


fileref = open("rainfall.txt","r")
fileref.close()

rainfile = open("rainfall.txt","r")
for aline in rainfile:
    values = aline.split()
    print (values[0], "had" values[1], "inches of rain")


    
    rainfile.close()
    

rainfile = open("rainfall.txt","r")
outfile = open("rainfallInCM.txt","w")
for aline in rainfile:
    values = aline.split()
    inches = float(values[1])
    cm = 2.54 * inches
    
    outfile.write(values[0]+""+str(cm)+"/n")

    rainfile.close()
    outfile.close()
    
import urlib.request                #counting lines in the head and the body
def countHead(url)
    page = urlib.request.urlopen(url)
    numHeadLines = 0
    
    line = page.readline().decode('utf-8')
    while '<head>' not in line:
         line = page.readline().decode('utf-8')
        
    line = page.readline().decode ('utf-8')
    while '<head>' not in line:
    numHeadLines = numHeadLines + 1
        line = page.readline().decode('utf-8')
        
    line = page.readline().decode('utf-8')
    while "<body>" not in line:
line = page.readline().decode('utf-8')





import turtle

maxHEIGHT = 0
maxAGE = 0

height = [75,74,74,74,74,64,66,66,67,67]
age = [83,64,63,56,67,85,79,67,90,80]

aList = list(zip(height, age))

def calcM(x,y):
    sumxy = 0
    sumxsquared = 0
    x = height
    y = age
    for i in range(len(y)):
        sumxy += y[i]*x[i]
        sumxsquared += x[i]**(2)
    n = len(y)

    xMean = sum(height)/len(height)
    yMean = sum(age)/len(age)

    nuem = (sumxy-(n*xMean*yMean))
    denom = (sumxsquared-(n*(xMean**(2))))

    m = neum/denom
    return m


if height > maxHEIGHT:
    maxHEIGHT = height
if age > maxAGE:
    maxAGE = age

t = turtle.Turtle()
screen = t.getscreen()
screen.setworldcoordinates(0,0,maxHEIGHT,maxAGE)

t.goto(0,0)
screen.tracer(5)

def plotRegression(qList,t):
        rList = dict(qList)

        M = calcM(x,y)

        t.up()
        for i in range(len(y)):
            t.goto(x[i],y[i])
            t.down()
            t.up()
            
plotRegression(aList,t)
screen.update()
screen.exitonclick()    














def mode (a):
countdict = {}
for item in a:
if item in countdict :
countdict[item] = countdict[item]+1
else
countdict[item] = 1





def mean (a):
  
    mean = sum(a) / len(a)
    return mean

def median (a):
    copylist = a[:]
    copylist.sort()
    if len(copylist)%2 ==0
        rightmid = len(copylist)//2
        leftmid = rightmid - 1
    else:
        mid = len(copylist)//2
        median = copylist[mid]
    return median


import math
def standardDev (a):
    theMean = mean(a)

    total = 0
    for item in a:
        difference = item - theMean
        diffsq = difference ** 2
        total = total + diffsq
    sdev = math.sqrt(total/(len(a)-1))
    return sdev


def getMax (a):
 maxsofar



KEYS
adict.keys()
*Returns a dict_keys object, ex:
  
  list(ages.keys())
  ['Hannah', 'Kelsey', 'Brenda', 'Rylea', 'David']

note that you have to put the list first

VALUES
adict.values()
*Returns a dict_values object

ITEMS
adict.items()
*Returns a dict_items object

GET
adict.get(k)
*Returnst he value associated with k; None otherwise

GET
adict.get(k,alt)
*Returns the value associated with k; alt otherwise

IN
key in adict
*Returns True if key is in the dictionary; False otherwise. ex:

  'Rylea' in ages
  True

NOT IN
key not in adict
*Returns Ture if key is not in the dictionary; False otherwise

INDEX
adict[key]
*Returns the value associated with key

DEL
del adict[key]
*Removes the entre from the dictionary. ex:

  del ages['David']

EXAMPLES OF ADDING AND MODIFYING VALUES IN A DICTIONARY
ages['David']
ages['Kelsey'] = 19
  *to add a key
ages['David'] = ages['David'] + 1
  *To add a value to the key

STRUCTURE OF A KEY
ages = {'David':45,'Brenda':46}


STANDARD DEVIATION
import math
def standardDev(alist):
  theMean = mean(alist)
  
  sum = 0
  for item in alist:
    difference = item - theMean
    diffsq = difference ** 2
    sum = sum + diffsq
  
  sdev = math.sqrt(sum/(len(alist)-1))
  return sdev













































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
    
    
    
    
    
    
    
    
