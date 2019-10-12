### Tower of Hanoi.
For three stands, this code will tell you the steps to take in order to move the discs from A to C, while keeping in mind the rules of the game.
```python
def move(from, to):
    print("Move disc from {} to {}!".format(f,t))# This code creates a function to move a disc from one stand to another

def moveVia(from, to, via):
    move(from, via)
    move(via,to)#This code creates a function to move a disc from one stand to another via a other stand

def hanoi(number_of_discs, via, to, from):
    if number_of_discs == 0:
        pass
    else:
        hanoi((number_of_discs-1), from, to, via)
        move(from, to)
        hanoi((number_of_discs-1), via, from, to)


```






