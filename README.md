



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
    
    
    
    
    
    
    
    
