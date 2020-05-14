### Tower of Hanoi - October 12 2019
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

### palindrome checker - April 16 2020
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
### Detection of numbers in pictures using MNIST data set
This code uses tensorflow and the mnist data set ( http://yann.lecun.com/exdb/mnist/ ), to create a CNN using pooling, convolutional and dense layers and effectively determine what number is present in an image. I have added frequent comments in the code to make it more understandable.
```python

import tensorflow as tf.#importing tensorflow

class myCallback(tf.keras.callbacks.Callback):  # this allows us to save on time by stopping the training when it reaches a sufficient accuracy
  def on_epoch_end(self, epoch, logs={}):
    if(logs.get('accuracy')>0.99):
      print("\ncancelling training)                
      self.model.stop_training = True
 
callbacks = myCallback()

mnist = tf.keras.datasets.mnist # importing and loading the dataset into training and test sets
(x_train, y_train),(x_test, y_test) = mnist.load_data()

x_train=x_train.reshape(60000, 28, 28, 1) # normalizing and reshaping the training data to make it suitable for the network
x_train  = x_train / 255.0

x_test = x_test.reshape(10000, 28, 28, 1)# normalizing and reshaping the test data to make it suitable for the network
x_test = x_test / 255.0

#now we get to the fun part! This code outlines the architecture of the network.
model = tf.keras.models.Sequential([
    tf.keras.layers.Conv2D(16, (3,3), activation='relu',kernel_initializer='he_uniform',
                           input_shape=(28, 28, 1)),
    tf.keras.layers.MaxPooling2D(2, 2),
    tf.keras.layers.Conv2D(32, (3,3), activation='relu', kernel_initializer='he_uniform'),
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Conv2D(64, (3,3), activation='relu', kernel_initializer='he_uniform'),
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Dense(512, activation='relu', kernel_initializer='he_uniform'),
  tf.keras.layers.Dense(10, activation='softmax'). #softmax as we have a lot of classes ( 10 to be exact)
]

model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy']).    #I prefer adam to sgd, and the loss is measured using sparse categorical crossentropy
              
model.fit(x_train, y_train, epochs=10, callbacks=[callbacks]) # training the model, takes some time

model.evaluate(x_test, ty_test) #tells us how accurate is the model

```

 





