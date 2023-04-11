#Object Oriented Programming Note #1

```python

#Example of a Class definition in python
class Person: 
    def__init__(self,name):
        self.name = name
    
    def __str__(self):
        return f"Person Object called: {self.name}"

```
## More notes: 
```class``` is a keyword in python to create a class
```__init__()``` is a base override

## Whats An Object and OOP?

In object-oriented programming, an object is an instance of a class that can be a variable, a function, a data structure, or a combination of these. Understanding objects and their properties is essential in both CS and OOP.

Object-Oriented Programming (OOP) is a programming practice that aims to design modular and reusable software systems. It does this by creating objects, which are instances of classes, and provides them with functionality to solve problems. OOP is an approach that focuses on the definition of data rather than the traditional 

## ```_repr__``` and ```str``` function

```__repr__``` is a special method in Python that allows an object to be printable. 

It is often used to provide a developer-friendly representation of an object, as opposed to the default string representation provided by ```__str__```.

```__repr__``` is automatically called when an object is passed to the built-in repr() function, or when it is printed using the ```print()``` function.

```str``` allows us to convert our object to a string 


