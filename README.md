1.Generate a list of all items in items_ordered that have more than one word
SELECT item from items_ordered where item LIKE '% %';
2.Generate the average per-unit price of all items that have more than one word
SELECT avg(price/quantity) from items_ordered where item LIKE '% %';
3.Select all customer id numbers and items with a quantity greater than 1
SELECT item, customerid from items_ordered where quantity > 1;
4.Return prices rounded to the nearest 10 (so 10, 20, 30, etc.)
SELECT round(price/10) from items_ordered;

1.Find the number of orders made and the total revenue raised by each customer if they have more than one purchase.
SELECT customerid, count(customerid), sum(price) from items_ordered GROUP by customerid HAVING count(customerid)>1;
2.Find the average price conditional on the customer paying less than $200.
SELECT avg(price/quantity), customerid from items_ordered GROUP by customerid HAVING sum(price) < 200;
3.Find the number of people in each state (from customers) if the state has more than one person in it.
SELECT customerid, state, count(customerid) from customers GROUP by state having count(customerid) > 1;
4.Find the average price of items that contain the letter E that sold more than one unit.
Select avg(price), item from items_ordered where item like '%e%' group by item having sum(quantity) > 1;

1)	How many orders did each customer make? Use the items_ordered table. Select the customerid, number of orders they made, and the sum of their orders.

2)	How many orders did each customer make? Use the items_ordered table. Select the customerid, number of orders they made, and the sum of their orders if they purchased more than 1 item.

3)	Write a query using a join to determine which items were ordered by each of the customers in the customers table. Select the customerid, firstname, lastname, order_date, item, and price for everything each customer purchased in the items_ordered table.

4)	Select the item that has a price closest to $100. Hint: Use nested select statements. 

5)	Select all item that had prices between $50 and $100. Only use items that have both a c and an e in them. 

6)	For all of the tents that were ordered in the items_ordered table, what is the price of the lowest tent?


1)	SELECT customerid, count(customerid), sum(price)
FROM items_ordered
GROUP BY customerid;

2)	SELECT customerid, count(customerid), sum(price)
FROM items_ordered
GROUP BY customerid
HAVING count(customerid) > 1;

3)	SELECT customers.customerid, customers.firstname, customers.lastname,
items_ordered.order_date, items_ordered.item, items_ordered.price
FROM customers INNER JOIN items_ordered ON customers.customerid = items_ordered.customerid
WHERE customers.customerid = items_ordered.customerid;

4)	SELECT min(abs(price-100)),item FROM items_ordered;

5)	SELECT item, price FROM items_ordered WHERE price BETWEEN 50 AND 100;

6)	SELECT min(price) FROM items_ordered WHERE item = 'Tent';



QUERY CLAUSE ORDER
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY


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
    
    
    
    
    
    
    
    
