---
title:  "Upcoming action items"
author: Clayton
categories: beginnerseries
---

So you want to start learning [Python](http://python.com) and developing programs and coding in general. There is no better time or place to start.

In this series we will take a basic look at what Python has to offer and to get used to a few things. We will start by knowing you already have Python installed. There are plenty of other articles on [installing Python](https://realpython.com/installing-python/).

Once we have Python installed we can begin. Open your terminal and type ```Python``` and we will enter the REPL. The REPL is short for Read, Eval, Print, Loop and the process is:

1. **Read**: Take user input
1. **Eval**: Evaluate the input
1. **Print**: show the output to the user
1. **Loop**: repeat

Within the REPL we can use this as a small playground for Python and test a few quick things out as needed. Many of Pythons commands we can use in the REPL. You can also import modules like the OS module for interacting with the Operating System.

To run your Python script we need to save your script with a py extention like ```myscript.py```. Remember not to save your the same name as a module or variable in your script. OS.py is not a valid file with working with the OS module since that is also the name of a module and will cause a syntax error.

Now that we know about the REPL and installing python, how do we run files? Sure there's no better way to learn that to see what has been done. Lets start with something simple.

Create a new file named ```myscript.py``` and open it in your text editor, and type the following into your file:

```python
# create the function
def hello(name):
    # take the input and use it in our print statment
    print(f'Hello {name}, its nice to see you!')


# create a variable as an input
yourname = input('Enter your name:')
# call the 'hello' function and send the variable 'yourname'
hello(yourname)
```

Now once in your terminal is in the same directory as your myscript.py file, lets run

```shell
python myscript.py
```

You should see the following:

![myscript-example](assets/images/myscript-example.gif)

Today we have learned how to install Python, took a look at the REPL, and how to run simple scripts.

This is only to get you started. Take a look at our [Resources](/Resources) page for further in depth learning.
