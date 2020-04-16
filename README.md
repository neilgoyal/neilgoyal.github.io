### Tower of Hanoi.
For three stands, this code will tell you the steps to take in order to move the discs from A to C, while keeping in mind the rules of the game.
```python
def move(from_, to):
    print("Move disc from {} to {}!".format(from_,to))# This code creates a function to move a disc from one stand to another

def moveVia(from_, to, via):
    move(from_, via)
    move(via,to)#This code creates a function to move a disc from one stand to another via a other stand

def hanoi(number_of_discs, via, to, from_):
    if number_of_discs == 0:# checks we dont start counting negative discs!
        pass
    else:
        hanoi((number_of_discs-1), from_, to, via)#Uses recursion to detect plausible routes and move on
        move(from_, to)
        hanoi((number_of_discs-1), via, from_, to)


```

### palindrome checker
This code will check if a number is a palindrome or not. An easier way like slicing can be used but the challenge was not to.
```python
num = int(input("enter number:"))
reverse = num
a=0
while reverse!= 0:
    a = a*10
    a = a+(reverse%10)
    reverse = int(reverse/10)
if a == num:
    print("yes")
else:
    print("no")
```







