## Snakify
## Part 1: While loop
### 1. List of Squares
For a given integer N, print all the squares of integer numbers where the square is less than or equal to N, in ascending order.
```.py
N = int(input())
a = 1
while a**2 <= N:
    print(a**2,end = " ")
    a += 1
```
### 2. Least divisor 
Given an integer not less than 2. Print its smallest integer divisor greater than 1.
```.py
a = int(input())
b = 2
while a%b != 0:
    b+=1
print(b)
```
### 3. The power of two 
For a given integer N, find the greatest integer x where 2x is less than or equal to N. Print the exponent value and the result of the expression 2x.
*Don't use the operation **.*
```.py
N = int(input())
x = 0
base = 2
while base <= N:
    x += 1
    base *= 2
    
print(x, base//2)
```
### 4. Morning jog
As a future athlete you just started your practice for an upcoming event. Given that on the first day you run x miles, and by the event you must be able to run y miles.
Calculate the number of days required for you to finally reach the required distance for the event, if you increases your distance each day by 10% from the previous day.

Print one integer representing the number of days to reach the required distance.
```.py
x_miles = int(input())
y_miles = int(input())
days = 1
while x_miles < y_miles:
    x_miles *= 1.1
    days  += 1
print(days)
```
### 5.The sum of the sequence
Determine the sum of all elements in the sequence, ending with the number 0.
```.py
total = 0
n = int(input())
while n != 0:
    total = total + n
    n = int(input())
print(total)
```
### 6.The average of the sequence
Determine the average of all elements of the sequence ending with the number 0.
```.py
count = 0
total = 0
a = int(input())
while a != 0:
    total += a
    count += 1
    a = int(input())
print(total/count)
```

