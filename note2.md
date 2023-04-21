

# Whats An Object and OOP?

In object-oriented programming, an object is an instance of a class that can be a variable, a function, a data structure, or a combination of these. Understanding objects and their properties is essential in both CS and OOP.

Object-Oriented Programming (OOP) is a programming practice that aims to design modular and reusable software systems. It does this by creating objects, which are instances of classes, and provides them with functionality to solve problems. OOP is an approach that focuses on the definition of data rather than the traditional

## Class and Attributes 

- A class is a blueprint or template for creating objects that defines its properties and methods.
- Classes can be used to create multiple instances of objects that share the same properties and behaviors.
- Classes can inherit properties and methods from other classes, allowing for code reuse and modularity.

- Attributes are data elements that belong to an object, defining its state or properties.
- Attributes can be public, private, or protected, controlling their accessibility from outside the class.
- Attributes can have default values, which are assigned when the object is created, or they can be set by the programmer during runtime.
- Attributes can be accessed and modified using methods called getters and setters, which allow for encapsulation and abstraction of the object's data.

![image](https://user-images.githubusercontent.com/129182651/233680828-edd41d02-5703-4d0b-af00-25037f4ed5f7.png)

### Example: 
```python
class Person:
    # Define the class attributes
    species = 'human'

    # Define the instance attributes
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Create an instance of the Person class
person1 = Person('John', 30)

# Access the instance attributes
print(person1.name)  # Output: John
print(person1.age)  # Output: 30

# Access the class attribute
print(Person.species)  # Output: human

```


# New functions/methods:

1. ## self() function
	- In Python, the first parameter of every method in a class is conventionally named "self" and it refers to the instance of the class on which the method is called. By using "self", methods can access and modify the attributes and methods of the instance it is bound to. Python automatically passes a reference to the object as the first argument when an instance method is called on an object. "self" is not a keyword, but a convention in Python, and changing its name is not recommended as it might cause confusion among developers who are familiar with the convention. This feature is specific to object-oriented programming in Python and not used in other programming paradigms.
 

		- ```python
			class Car:
				def __init__(self, make, model, year):
					self.make = make
					self.model = model
					self.year = year
					self.mileage = 0

2. ## ```__str__``` and ```__repr__```
	
	- In Python, the __str__ and __repr__ functions are used to define how an object should be represented as a string. The __str__ method returns a readable string representation of an object, while the __repr__ method returns a string representation of an object that can be used to recreate the object. When you print an object, Python calls the __str__ method to get a string representation of the object. If the __str__ method is not defined, Python falls back to calling the __repr__ method. It's a good practice to define both methods for your classes, but if you have to choose only one, it's usually better to define the __repr__ method, as it provides a more complete representation of the object.
		
		- ```python
			class Person:
			    def __init__(self, name, age):
				self.name = name
				self.age = age

			    def __str__(self):
				return f"{self.name} is {self.age} years old"

			    def __repr__(self):
				return f"Person('{self.name}', {self.age})"

			p = Person("Aaron B", 30)
			print(str(p))     # Output: Aaron B is 16 years old
			print(repr(p))    # Output: Person('Aaron', 16)
  
3. ## ```__init__```
	
	- In Python, the __init__ method is a special method that is called automatically when an object of a class is created. It is used to initialize the instance variables of an object with values passed as arguments to the constructor. The __init__ method is also called a constructor method, as it constructs and initializes the object. It takes self as the first argument, which refers to the object being created. It can take any number of additional arguments, which are used to initialize the instance variables of the object. By defining the __init__ method, you can customize the initialization process of your objects and ensure that they start with the correct initial values.
	 	
		- ```python 
		 	class Dog:
			    def __init__(self, name, breed):
				self.name = name
				self.breed = breed

			    def bark(self):
				print(f"{self.name} ({self.breed}) is barking!")

			my_dog = Dog("Dixie", "Labrador Retriever")
			my_dog.bark()  # Output: Fido (Labrador Retriever) is barking!

			```
4. ## ```super()```
- ```super()``` is a built-in function in Python used to refer to the parent class of a derived class.
- It allows the derived class to access methods and properties of the parent class, and can be used to call its methods.
- ```super()``` takes two arguments: the first is the class that we want to refer to, and the second is the instance of the class.
- By using ```super()```, we can avoid hardcoding the parent class name in the derived class and make the code more flexible and maintainable.
```super()``` is commonly used in method overriding, where we want to customize the behavior of a method from the parent class.
- We can also use ```super()``` to call the constructor of the parent class in the derived class, using ```super().__init__()``` syntax.
5. ## ```__iter__()``` and ```__next__()```
- ```__iter__()``` allows our object to be iterable, when invoked upon (ex. By a for loop), it will called the method. Commonly just returns it self
- ```__next__()``` allows us to get to the next value when iterating
	- Common Practice: 
		- set an index attribute to -1
		- increment the index attribute by 1 until self.__index is equal to length of sequence
		- when the end is reached, raise StopIteration
```python
class MyRange:
    def __init__(self, start, end):
        self.start = start
        self.end = end

    def __iter__(self):
        self.current = self.start
        return self

    def __next__(self):
        if self.current < self.end:
            value = self.current
            self.current += 1
            return value
        else:
            raise StopIteration 
```

# Create an instance of MyRange and iterate over its values
my_range = MyRange(1, 5)
for num in my_range:
    print(num)



## Overriding

- Overriding is a concept in object-oriented programming that allows a subclass to provide its own implementation of a method that is already defined in its superclass.

- This means that the subclass method "overrides" the superclass method, and when the method is called on an instance of the subclass, the subclass implementation is used instead of the superclass implementation.

- To override a method in Python, you simply define a method with the same name in the subclass as the method you want to override in the superclass.

- When the method is called on an instance of the subclass, Python will automatically use the subclass implementation of the method, rather than the superclass implementation.

- Overriding is useful when you want to customize the behavior of a method for a specific subclass, while still inheriting the rest of the behavior from the superclass.

- Two methods with the same method name and parameters

### Example of overriding
```python
class Vehicle:
    def __init__(self, color):
        self.color = color

    def start_engine(self):
        print("Starting engine...")

class Car(Vehicle):
    def start_engine(self):
        print("Insert key, turn ignition...")

class Motorcycle(Vehicle):
    def start_engine(self):
        print("Pull clutch lever, press start button...")

my_vehicle = Vehicle("blue")
my_car = Car("red")
my_motorcycle = Motorcycle("green")

my_vehicle.start_engine()  # Output: Starting engine...
my_car.start_engine()      # Output: Insert key, turn ignition...
my_motorcycle.start_engine()  # Output: Pull clutch lever, press start button...

```

## Overloading 

- Overloading refers to the ability to define a single function with multiple implementations that differ in the number or type of arguments.
- In Python, you can overload functions using default arguments, variable-length arguments, or by using the "args" and "kwargs" syntax.
- Overloading allows for more flexible and readable code, as well as improved code reuse.
- **Python does not support method overloading** based on the return type of the function.
- In Python, operator overloading is also possible, allowing you to define the behavior of built-in operators (e.g., +, -, *, /) for custom classes.
- Two methods in one class that have the same method name, but different parameters

## Polymorphism 

- Polymorphism is a concept in object-oriented programming that allows objects of different classes to be treated as if they were of the same class.
- Polymorphism allows you to write code that can work with objects of different classes, as long as they implement the same methods or have the same attributes.
- Polymorphism is achieved through inheritance and method overriding, where a subclass can provide its own implementation of a method that is already defined in its superclass.
- Polymorphism makes code more flexible and reusable, by allowing you to write generic code that can work with many different types of objects, rather than having to write specialized code for each type.
- Polymorphism is a key feature of many object-oriented programming languages, including Python, and is used extensively in libraries and frameworks to provide generic solutions that can be customized for specific use cases.
- Poly = Many, morphism= forms
## Encapsulation

- Its purpose is to hide the implementation details of a class from its users, while providing a clean and consistent interface for interacting with the class.
- Access modifiers such as public, private, and protected are used to control the visibility of class members.
- Encapsulation helps to promote data integrity and maintainability by providing a clear separation between the implementation details of a class and its external interface.
- Encapsulation is a key principle of object-oriented programming.
- It's prefix is __
 
 ### Why use encapsulation? 
 Encapsulation is used for data protection, restricting certain mathoeds to be callable

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

 ## Inheritance
 
- Inheritance is a fundamental concept in object-oriented programming that allows creating new classes based on existing classes.
- The new class is called a child class (or derived class), and the existing class is called the parent class (or base class).
- The child class inherits all the properties and methods of the parent class, and can also add new ones or override existing ones.
- Inheritance provides a way to reuse code and avoid duplication, as well as to organize and modularize code into smaller, more manageable units.
- In Python, we can define a child class by specifying the parent class name in parentheses after the child class name in the class definition.
- Child classes can access parent class methods and properties using the ```super()``` function or by directly calling them using the parent class name.
- Multiple inheritance is a feature that allows a class to inherit from multiple parent classes, and is supported in Python by specifying multiple parent class names in parentheses after the child class name.

## Types of Inheritance

![image](https://user-images.githubusercontent.com/129182651/232961614-748c64f8-d1f9-4852-87f3-9d1f57f12b58.png)

### Examples of Multi-generational

```python
class Grandparent:
    def grandparent_method(self):
        print("This is a method of the Grandparent class")

class Parent(Grandparent):
    def parent_method(self):
        print("This is a method of the Parent class")

class Child(Parent):
    def child_method(self):
        print("This is a method of the Child class")

class Grandchild(Child):
    def grandchild_method(self):
        print("This is a method of the Grandchild class")

gc = Grandchild()
gc.grandchild_method() # This is a method of the Grandchild class
gc.child_method() # This is a method of the Child class
gc.parent_method() # This is a method of the Parent class
gc.grandparent_method() # This is a method of the Grandparent class

``` 
### Example of Multi-parent

```python
class Parent1:
    def method1(self):
        print("This is a method of Parent1 class")

class Parent2:
    def method2(self):
        print("This is a method of Parent2 class")

class Child(Parent1, Parent2):
    def child_method(self):
        print("This is a method of Child class")

c = Child()
c.method1() # This is a method of Parent1 class
c.method2() # This is a method of Parent2 class
c.child_method() # This is a method of Child class
```

Final notes: 
- A setter and a getter
- A setter updates an attribute in a controlled way
- A getter accesses attributes in a safe way, some attributes shouldn’t be accessed 
- Getter accesses encapsulated attributes and controls which attributes are accessible 
- Method is a fancy word for a function that belongs to an object/data
- __int__ is a special built in naming function, meaning the name of it can’t be changed
- Left side is the argument and right side is the function 




    
