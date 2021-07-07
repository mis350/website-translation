---
# Page title
title: Python Review

# Title for the menu link if you wish to use a shorter link title, otherwise remove this option.
linktitle: Python

# Date page published
date: 2021-03-23

# Academic page type (do not modify).
type: book

# Position of this page in the menu. Remove this option to sort alphabetically.
weight: 2

draft: False

---

{{% callout note %}}
Slides for this section can be found [here]({{< ref "/slides/350/python/index.md" >}})
{{% /callout %}}

## Prerequisite

Having completed and introductory course in programming is required. It doesn't have to be in Python as the ideas are still the same.

## The Review

Given the limited time we have in this course, we will go over some necessary topics on Python, but will defer the review to the Lab and for you to read some online tutorials on the language.

If your prior programming course was on a different languages, for example Visual Basic or Java, then the same idea apply in Python. There are variables, functions, loops, and if statements as you have come to expect and use. The only difference is that you need to learn the syntax. For example, in VB you might write and if statement like this:
```
If x > 5 Then
    ` Do something like display this message
    MsgBox("the condition is True!")
End If
```

In Python, it would by like so:
```python
if c > 5:
    # Do something like display this message
    print("The condition is True!")
```

## Online Resources

Go through any one of following online references and it will be suffecient in reviewing the Python language syntax:

1. [Python for You and Me](https://pymbook.readthedocs.io/en/latest/)
2. [Learn Python](https://www.learnpython.org/)
3. [The Python Guru](https://thepythonguru.com/)
4. [Python Basics](https://pythonbasics.org/)

## New Topics

There are a few topics that we haven't covered in our introduction to Python which we will cover in this course:

### Exceptions

Exceptions are like if statements, they perform a task conditionally. The difference is in how the condition is evaluated.

In if statements, the condition is checked before the execution of the conditional code, therefore, the condition always comes before the conditional code:
```python
if condition:
    # perform conditional code
```
Whereas with exception, the condition is in the form of the existance of an exception (also known as an error). So the computer would perform some code normally, but we instruct the computer to perform the conditional code if a specific error occured while executing the code. So the condition is tied to the occurance of an error (or exceptional) event:
```python
try: #1
    received_data = socket.read() #2
except IOException as ioe: #3
    print("Connection disconnected") #4
```

To use exceptions in python we have to write lines #1 and #3. The code between them is observed by the computer. Here, we instructed the computer to read a network socket and store the received data. The try/except tells the computer while executing #2, if an error of the type IOException occurs, like network disconnection, then perform #4.

The only situation in which #4 is performed is when there is an error in reading the network causing an IOException to occur. Please read the following [article on exceptions](https://pythonbasics.org/try-except/).

### List Comprehensions

One of the common tasks performed on lists is to process the data in them and construct other lists. For example, the following code would create a new list from an existing one containing only even numbers:

```python
data = [2, 3, 4, 5, 10, 34, 1]
even_numbers = []
for x in data:
    if x % 2 == 0:
        even_numbers.append(x)
```

With list comprehensions, we can perform the same thing with just a single line:

```python
data = [2, 3, 4, 5, 10, 34, 1]
even_numbers = [x for x in data if x % 2 == 0]
```

Please read the following [article on list comprehensions](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python).

### Object Oriented Programming

Object Oriented Programming (OOP) is a way of structuring your program. So far, we learned to write programs as a single unit, where all the code is in a single file that performs all the requirements.

Then we learned how to structure our code into functions and organize them in different files. This is called structural programming is an improvement on how we learned to program initially.

Another improvement over structual programming is Object Oriented Programming (OOP). The idea is similar to structural programming in which we reorganize the code. However, it is different in the way we organize and group things. In structural programming, we only created functions that performed tasks and tried to group releated tasks together in the same file. With object oriented programming, we group related **data and functions** together and put them in a single unit called a call. We also cannot directly use the class, we must create an object (also known as an instance) of this class that contains a copy of the data and functions.

Classes define how an object will look like and are like a blue print of a building. We cannot live in the blue print! we must construct the building first based on the drawing. The same is with classes. The computer cannot use a class, however, we can instruct the computer to create an object based on the definition described in the class.

An example of a class would be Human. When you see a human, you can recognize them as they all have heads, hands, legs, and very similar general features. However, each human is unique in that they have their own name, color, fingerprint, age ...etc. Each individual is equivalent to an object in OOP, whereas the human race is equivalent to a class.

In addition to the organizational benefits of OOP, like hiding complexity (called encapsulation), it also introduces the concept of inheritence where we can derive one class from another, which allows us to reuse code. **We will be using OOP and espciailly inheritence heavily in this course**. For more details, please refer to chapter 10 of the python textbook and read the [following article](https://realpython.com/python3-object-oriented-programming/)

[{{< icon name="youtube" pack="fab" >}}Watch this YouTube video list](https://www.youtube.com/playlist?list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc) for an excellent introduction to OOP


{{< youtube ZDa-Z5JzLYM >}}

## Review Questions

- What are exceptions? What can we use them for?
- What are list comprehensions?
- What is OOP? What are its benefits?
- What is inheritance? Give an example where we have used it in this course (For final)