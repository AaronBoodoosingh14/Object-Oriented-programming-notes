
## More notes: 
```class``` is a keyword in python to create a class
```__init__()``` is a base override

## Whats An Object and OOP?

In object-oriented programming, an object is an instance of a class that can be a variable, a function, a data structure, or a combination of these. Understanding objects and their properties is essential in both CS and OOP.

Object-Oriented Programming (OOP) is a programming practice that aims to design modular and reusable software systems. It does this by creating objects, which are instances of classes, and provides them with functionality to solve problems. OOP is an approach that focuses on the definition of data rather than the traditional 

## ```__repr__``` and ```__str__``` function

```__repr__``` is a special method in Python that allows an object to be printable. 

It is often used to provide a developer-friendly representation of an object, as opposed to the default string representation provided by ```__str__```.

```__repr__``` is automatically called when an object is passed to the built-in repr() function, or when it is printed using the ```print()``` function.

```__str__``` allows us to convert our object to a string 

## Polymorphism and Overriding  

* A method that can be used across different classes and object that is dependent on the parameters.

* Different Classes (non-inherited) can have the same named methods (Simple) → Polymorphism

* Within a set of inherited classes have the same methods

We can have Two different classes have a same attributes and methods
A child of a parent have an overrided method where the child would utilize the method differently.
These are the two fundamental concepts of overriding and polymorphism in Python

### Examples:

```python

class Bear:
    def sound(self):
        print("Groarrr")
 
class Dog:
    def sound(self):
        print("Woof woof!")
 
def makeSound(animalType):
    animalType.sound()
    
bearObj = Bear()
dogObj = Dog()
 
makeSound(bearObj)
makeSound(dogObj)
   
   ```
   
 ```python
 
 class Dog:
	def __init__(self,name):
		self.__name = name
	
	def __str__(self):
		return “Woof, I’m %s.” % self.__name

corgi = Dog(“Tobasco”)
print(corgi) → “Woof, I’m Tobasco.”

```
 Overloading is illegal in python, but is still a form of polymorphisim
 




    
