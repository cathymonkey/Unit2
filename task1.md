```.py
#guess a number between 1-100
import random
Times = []
def run():

    print("Hi player A, remember you can only reply","low,","high","or This is the number!")
    num =  random.randint(1,99)
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
            B_num = int(B_num1 + round(abs((B_num - B_num0))/2))
            print("Guess again!\n{}".format(B_num))
            B_num0 = B_num1
            B_num1 = B_num

        elif B_num > num:
            hint == print("high")
            B_num = int(B_num1 - round(abs((B_num - B_num0)) / 2))
            print("Guess again!\n{}".format(B_num))
            B_num0 = B_num1
            B_num1= B_num


i = 0
while i<50:
    run()
    i+=1

print(Times)
average = sum(Times)/i
print(average)
