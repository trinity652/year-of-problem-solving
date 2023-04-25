 Sure, here's a quick reference guide for some common Python syntax and operations:

### Python Basics
- **Variables**: Variables are used to store data values. Python does not require declaring the variable type, and the type is determined based on the value assigned to it.
    ```
    x = 5
    y = "Hello, World!"
    ```
- **Print**: The print() function is used to output data to the console.
    ```
    print("Hello, World!")
    ```
- **Input**: The input() function is used to accept user input.
    ```
    name = input("What is your name? ")
    ```
- **Control Flow**: Python supports control flow statements such as if-else, while, for, and break/continue statements.
    ```
    if x > 0:
        print("Positive")
    else:
        print("Non-positive")
    
    while x > 0:
        print(x)
        x -= 1
    
    for i in range(10):
        print(i)
        
    for char in "Hello":
        print(char)
        
    for num in [1, 2, 3]:
        print(num)
    
    for i in range(10):
        if i == 5:
            break
        print(i)
        
    for i in range(10):
        if i == 5:
            continue
        print(i)

### Functions and Modules
- **Functions**: Functions are blocks of code that perform a specific task. They can take parameters as input and return values as output.
    ```
    def greet(name):
        print("Hello, " + name + "!")
    
    greet("John")
    ```
- **Modules**: Modules are used to organize Python code into reusable blocks. Python has a large number of built-in modules, and you can also create your own modules.
    ```
    import math
    print(math.pi)
    
    import mymodule
    mymodule.greet("John")
    ```
    
### Object-Oriented Programming
- **Classes**: Classes are used to create objects that have properties (attributes) and methods.
    ```
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age
        
        def greet(self):
            print("Hello, my name is " + self.name)
    
    p = Person("John", 30)
    p.greet()
    ```
- **Inheritance**: Inheritance is a way to create a new class from an existing class, inheriting all its properties and methods.
    ```
    class Student(Person):
        def __init__(self, name, age, student_id):
            super().__init__(name, age)
            self.student_id = student_id
        
        def study(self):
            print(self.name + " is studying.")
    
    s = Student("Alice", 20, "1234")
    s.greet()
    s.study()
    ```

### File Handling and Exception Handling
- **File Handling**: Python has built-in functions for reading from and writing to files.
    ```
    f = open("myfile.txt", "w")
    f.write("Hello, World!")
    f.close()
    
    f = open("myfile.txt", "r")
    print(f.read())
    f.close()
    ```
- **Exception Handling**: Python has a try-except block for handling exceptions.
    ```
    try:
        x = int(input("Enter a number: "))
        y = 10 / x
        print(y)
    except ValueError:
        print("Invalid input")
    except ZeroDivisionError:
        print("Cannot divide by zero")
    ```

### Data Structures in Python
- **Lists**: Lists are used to store multiple items in a single