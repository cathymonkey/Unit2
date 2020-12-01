## Day 1
**Task 1**
```.py
#Find the two entries that sum to 2020; what do you get if you multiply them together?

data = open("Input","r").read().splitlines()
num = []
for i in data:
    num.append(int(i))

for i in range(len(num)):
    for j in range(len(num)):
        if i != j and num[i] + num[j] == 2020:
            print(num[i],num[j])
            print(num[i]*num[j])

#Result: Two entries are 1184 and 836 and their product is 989824.

```
**Task 2**
```.py
#what is the product of the three entries that sum to 2020?

data = open("Input_2","r").read().splitlines()

num = []
for i in data:
    num.append(int(i))
for i in range(len(num)):
    for j in range(len(num)):
        for k in range(len(num)):
            if i!=j!=k and num[i]+num[j]+num[k] == 2020:
                print(num[i],num[j],num[k])
                print(num[i]*num[j]*num[k])
                
#Result: Three entries are 1614,210 and 196 and their product is 66432240.
```
**I think there maybe other ways to solve the question like searching from the beginning and end at the same time but I'm not sure about it.**
                
                
                
                
