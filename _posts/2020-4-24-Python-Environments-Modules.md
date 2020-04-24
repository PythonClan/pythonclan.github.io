---
title:  "Python Environments & Modules"
author: Clayton
categories: beginnerseries
---

By default when you install Python and install modules you are installing these globally so you can use those modules in any script located anywhere on the system. 

## The Python Package Index (PyPi)

[PyPi](https://pypi.org/) is the repository for software for the Python language and also a way for other Python developers to distribute their software.

To easily install the packages found on PyPi you can use a tool called pip. [PIP](https://pip.pypa.io/en/stable/) is a Python Package Installer.

To get started you need to download pip by doing:

```shell
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```

Then we need to install pip.

```shell
python get-pip.py
```

If you have further issues you can read the [documentation](https://pip.pypa.io/en/stable/installing/)

## Installing modules and Virtual Environments

I have a great article that talks about setting up your [Virtual Environments](https://claytonerrington.com/blog/Python-Virtual-Environments/) that you can read. A virtual environment with Python creates a sub-install type system that you can activate to run Python programs in a container type area that is not affected System wide.

When installing modules from the default shell we are installing them globally. Sometimes we need this but other times we are working on projects that require a certain version of a module, or testing a new version, or even just playing with new concepts that we don't want to affect globally on our system. This is the beauty of virtual environments.

Now that we know about pip and environments lets start a small project. This next part is taken from a great [article](https://docs.python-guide.org/dev/virtualenvs/) about virtual environments and goes a little deeper than what I do here for our needs. 

Use ```pip``` to install ```pipenv```. This is another virtual environment tool we can use in Python. 

```shell
pip install pipenv
```

This will download and install ```pipenv``` on your machine. Now lets create a folder for our project and install the requests module.

```shell
mkdir project_folder
pipenv install requests
```

Pipenv will install the request module in our new project and will keep track of the dependencies on a per-project basis. Pipenv will generate a new pipfile that is used to keep track of the dependencies and if you need to share them with others.

### Using our virtual packages

Once pipenv is done installing Requests we can create a simple ```main.py``` file to use:

```python
import requests

response = requests.get('https://httpbin.org/ip')

print('Your IP is {0}'.format(response.json()['origin']))
```

Next we can run our script using ```pipenv run```

```shell
pipenv run python main.py
```

You should get a similar response like:

```shell
Your IP is 8.8.8.8
```

By using ```pipenv run``` will ensure you are running your script with the available packages you've installed for the virtual environment.

## Next Steps

Today we saw some ways to import modules into your script so your Python scripts knows what other functions to use in your main process. Also how to create virtual environments to keep projects separate incase different versions are needed on one machine or a group project that only needs to install modules for that project.

There is a whole suite called [Anaconda](https://www.anaconda.com/) that is used for Data Science and Machine Learning but also has great virtual environment setups. The install comes with other great tools like Spyder, Jupyter, and conda that help speed up the process and comes with pre-installed modules for data science like NumPy, SciPy, Pandas, Matplotlib, TensorFlow and more.
