### 001
**Given 2 numbers, A and B, Output TRUE if one of them is 10 or if their sum is 10.**
```.py
def Makes10(a,b):
    if a == 10 or b == 10:
        return True
    elif a+b == 10:
        return True
    else:
        return False
print(Makes10(9,10))
print(Makes10(9,9))
print(Makes10(1,9))
```

### 002
**Given three int values, A, B, and C, output the largest.**
```.py
def IntMax(a,b,c):
    if b > a:
        if b >= c:
            max = b
        else:
            max = c
    else:
        if a > c:
            max = a
        else:
            max = c
    return max
print(IntMax(1,2,3))
print(IntMax(1,3,2))
print(IntMax(3,2,1))

```

### 003
**Given an integer N, print all the integers from 0 to N.** 

**[HL] show also the addition of the numbers.**
```.py
def rangeN(n):
    total = 0
    for i in range(n+1):
        total = (n*(n+1))/2
        print(i)
    print (total)
rangeN(6)
```

### 004
**Given an integer N, show all its factors.** 

[HL] show also the addition of the factors show if the result is the same as N.**

```.py
def perfectN(a):
    total = 0
    for i in range(1,a,1):
        if a % i == 0:
            print(i)
            total += i
    if total == a:
        print("Sum of factors is:",a)
perfectN(6)
```

### 005
**Given an integer N, show the multiplication table.**
```.py
def tableM(n):
    for i in range(1,10):
        x = n * i
        print(n, "*", i ,"=",x)
tableM(2)
```
### 6
**Output TRUE if the given string begins with 'mix', except the 'm' can be anything, so 'pix', '9ix'..all count.**
```.py
def MixStart(s):
   if s[1] == "i" and s[2] == "x":
       return True
   else:
       return False
print(MixStart("mix snacks"))
print(MixStart("pix snacks"))
print(MixStart("piz snacks"))
```
### 7
**Given a string, output each letter with its index.**
```.py
def letters(s):
    for i in range(len(s)):
        print(i,"->",s[i])
print(letters("hello"))
```
### 8 
**Given an array of integers, find the largest absolute value.  Tip: you can use the abs() function.**
```.py
def maxAbs(a):
    max = 0
    for i in range(len(a)):
        if abs(a[i]) > max:
            max = abs(a[i])
    print(max)
maxAbs([-4,5,6,7])
maxAbs([-1,0,1])
maxAbs([-100, 0, 3,-200])
```
### 9 
**Given an array of sorted integers, find the missing number.**
```.py
def missingNumber(a):
    for i in range(len(a)-1):
        if a[i] != a[i+1] - 1:
            miss_number = a[i]+1
    print(miss_number)
missingNumber([1,2,3,5,6,7])
missingNumber([4,5,6,8,9,10])
missingNumber([73, 74, 75, 76, 78, 79])
```
### 10
**??????**
```.py
def maxNeighbour(numbers):
    max_diff = 0
    for i in range(len(numbers)-1):
        diff = abs(numbers[i]-numbers[i+1])
        if diff > max_diff:
            max_diff = diff
    return max_diff

print(maxNeighbour([1,2,3,5,6,7]))
print(maxNeighbour([10,0]))
```
### 11
**Given an array of numbers, output TRUE if the array is length 1 or more, and the first element and the last element are equal. Otherwise output FALSE.**
```.py
def SameFirstLast(x):
    return len(x) and x[0] == x[-1]
print(SameFirstLast([1,2,3]))
print(SameFirstLast([1,2,3,1]))
print(SameFirstLast([1,2,1]))
```
### 12
**Given an array of words, find the average word length.**
```.py

def wordlength(x):
    sum = 0
    for i in range(len(x)):
        sum += len(x[i])
    avg = sum/len(x)
    return avg
print(wordlength(["home", "car", "travel", "beach"]))
print(wordlength(["sun","sat","cut","can"]))
print(wordlength(["police", "abacus"]))
```






