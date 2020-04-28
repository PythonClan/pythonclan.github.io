---
title:  "Python Random Passwords"
author: Clayton
categories: examples
tags: beginner
---

## Setting up the basics

For the first item in our beginner series we'd like to talk about random password generating. This will allow us to see how to import modules, use functions, and generate some arguments for our script. All common things we'd like to use when creating then distributing the script to others and allow a fluid option in the script.

To begin, what we need:
- random
- string

We start by import the modules we need.

```python
import random
import string
```

I want to build our code that will create our password into a function. To do so we define our function with ```def``` and then the name like so:

```python
def randPass():
```

Next we need to create our password character string. The ```string``` module gives us the ability to get a collection of the letters, numbers and punctuation.

```python
password_characters = string.ascii_letters + string.digits + string.punctuation
```

This variable puts all the possible characters we will use together in one variable. Next we will need to return our function for the final output.

```python
return ''.join(random.choice(password_characters) for i in range(length))
```

We start with a blank string and join it with ```random.choice``` to choose our password characters for the length of our password defined by length. Lets add this variable to our function so we can pass this value along later dynamically in a way. At our ```randPass()``` function lets add ```length``` to the function like so:

```python
def randPass(length):
```

Our full randPass.py script so far should look like so:

```python
import random
import string

def randPass(length=8):
    password_characters = string.ascii_letters + string.digits + string.punctuation
    return ''.join(random.choice(password_characters) for i in range(length))
```

Now we just need to call our function outside of the ```def``` and we can get a random string which we can use for a password. By setting ```length=8``` in our function we are giving it a default value. Now we can run our function like so

```python
# generate an 8 character string
randPass()

# generate a 15 character string
randPass(15)
```

## Adding some command line arguments

So what is all the code and what does this line mean?

```python
if __name__ == "__main__":
```

If the script is called directly we will run some additional code and run our main process. For now we want to import ```argparse``` and setup some arguments. In doing so we'll also need to update our main ```randPass()``` function.

```python
    import argparse
    parser = argparse.ArgumentParser(description="Random Password Generator")
    parser.add_argument("-l", "--length", type=int, help="Length of password in integer, default is 14", default=14)
    parser.add_argument("-n", "--numbers", action='store_true', help="Add numbers to password")
    parser.add_argument("-a", "--alpha", action='store_true',  help="Add mixed case alpha characters to password")
    parser.add_argument("-p", "--punctuation", action='store_true', help="Add punctuation characters to password")
    parser.add_argument("-c", "--count", type=int, help="Number of passwords to generate", default=1)

    # gather arguments
    args = parser.parse_args()
    length = args.length
    numbers = args.numbers
    alpha = args.alpha
    punctuation = args.punctuation
    count = args.count
```

With the addition of the arguments, we added command line arguments for length, numbers, alpha, punctuation, and how many passwords to create.

We will print some pretty lines to the console too

```python
    # add our choices together to then print them in the result. 
    choices = ""
    if numbers:
        choices += " numbers"
    
    if alpha:
        choices += " letters"
    
    if punctuation:
        choices += " special characters"

    if choices == "":
        choices = " numbers, letters, and special characters"

    # print line stating the number or random strings, the length and the choices of the password
    print(f"Generating {count} Random String password of {length} characters with{choices}")
    # get the 'count' and for make a new password until the count is finished
```

Next we need to handle the number of passwords the user wants.

```python
    for x in range(count):
        # start x at 1 then add 1 to x
        x += 1
        # generate the password
        password = randPass(length, numbers, alpha, punctuation)
        # output the password to the screen
        print(f"{x} : {password}")
```

Once completed we can now run our script in the console. With no arguments we will create a random string with 14 characters as in our default length argument and the characters would be all possible string options.

```shell
> python randpass.py

Generating 1 Random String password of 14 characters with
1 : -k1b.boKDy%I<Q
```

## How to use the arguments

By default Argparse generates a great -h or help command.

```shell
> python randpass.py -h

usage: randpass.py [-h] [-l LENGTH] [-n] [-a] [-p] [-c COUNT]

Random Password Generator

optional arguments:
  -h, --help            show this help message and exit
  -l LENGTH, --length LENGTH
                        Length of password in integer, default is 14
  -n, --numbers         Add numbers to password
  -a, --alpha           Add mixed case alpha characters to password
  -p, --punctuation     Add punctuation characters to password
  -c COUNT, --count COUNT
                        Number of passwords to generate
```

With the arguments in the script we can create a password with the characters, numbers, punctuation, and the number of passwords to make.

Lets create 5 passwords with a length of 20 and use alpha characters and numbers. 

```shell
> python randpass.py -l 20 -a -n -c 5

Generating 5 Random String password of 20 characters with numbers letters
1 : jSzLlvxT3ExvRbzQErav
2 : ap04tS5sMyg1wnrwUHz5
3 : lH44j5M7kZla9YqtoU1U
4 : HauT0Uz7aEYkVAEYKeP2
5 : 6dwv7ncmBNAbZmUD3T6o
```
