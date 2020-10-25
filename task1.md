```.py
    #guess a number between 1-100
    print("Hi player A, remember you can only reply","low,","high","or This is the number!")
    A_num = int(input("Now,please enter a number from 1-100 :"))
    print("\n"*100)
    B_num= int(input("Player B, please guess a number!(Guess 50 first!!)\n"))
    B_num0 = 100
    B_num1 = 50

    while True:
        hint = input("Player A: ")

        if B_num == A_num:
            hint = "This is the number!"
            break

        elif hint == "low":
            B_num = int(B_num1 + int(abs((B_num - B_num0)+1) / 2))
            print("Guess again!\n{}".format(B_num))
            B_num0 = B_num1
            B_num1 = B_num

        elif hint == "high":
            B_num = int(B_num1 - int(abs((B_num - B_num0)-1) / 2))
            print("Guess again!\n{}".format(B_num))
            B_num0 = B_num1
            B_num1= B_num
            
```.py
Times = []
import random
print("Hi player A, remember you can only reply","low,","high","or This is the number!")
num =  random.randint(1,100)
A_num = input(("Now,please enter a number from 1-100:{}").format(num))


print("\n"*100)
B_num= (input("Player B, please guess a number!(Guess 50 first!!)"))
B_num = 50
print(B_num)
B_num0 = 100
B_num1 = 50
count = 0

while True:
    count += 1
    hint = input("Player A:")

    if B_num == num:
        hint = print("This is the number!")
        print("You only guess {}times".format(count))
        Times.append(count)
        break

    elif B_num < num:
        hint == print("low")
        print(hint)
        B_num = int(B_num1 + int(abs((B_num - B_num0)+1) / 2))
        print("Guess again!\n{}".format(B_num))
        B_num0 = B_num1
        B_num1 = B_num

    elif B_num > num:
        hint == print("high")
        B_num = int(B_num1 - int(abs((B_num - B_num0)-1) / 2))
        print("Guess again!\n{}".format(B_num))
        B_num0 = B_num1
        B_num1= B_num
print(Times)
