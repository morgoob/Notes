# Python Basics

**Everything in Python is an object, objects have attributes and functions.**

To find out the type of an object:

`type(objName)`

# **Numbers**

---

### **Types of Numbers**

There are two types of numbers in Python: **integers** and **floats**.

### **Division**

- Regular division (**`/`**) always returns a float.
- Integer division (**`//`**) returns an integer.

### **Exponentiation**

The power (**`**`**) operator is used for exponentiation. For example, **`2 ** 2`** equals 4.

### **Modulo**

The modulo (**`%`**) operator calculates the remainder. For example, **`10 % 3`** equals 1.

# **Strings**

---

### **String Creation**

Strings can be enclosed in single or double quotes unless the string itself contains un-escaped single quotes.

### **Backwards Access**

- Access the last character: **`str[-1]`**
- Access the second to last character: **`str[-2]`**

### **Slicing**

Slicing allows you to extract parts of a string using the syntax **`String[start:end]`** (where the end is not inclusive). For example:

```python
str = "Morgan"
str[0:3] == "Mor"
str[2:-1] == "rga"
```

### **Concatenation**

You can concatenate strings using the **`+`** operator. For example:

```python
str1 = "Morgan"
str2 = "Lloyd"
str3 = str1 + str2  # str3 will be "MorganLloyd"
```

### **Multiplication**

Strings can be multiplied by an integer to repeat them. For example:

```python
str = "Morgan"
str * 3 == "MorganMorganMorgan"
```

### **String Methods**

- **`str.upper()`** converts the string to uppercase.
- **`str.split()`** splits a string into a list based on a delimiter.
- **`len(str)`** returns the length of the string.

### **String Formatting**

### F-Strings (Ideal)

```python
num1 = 1234.56789
num2 = 9876.54321
print(f'num1: {num1}, num2: {num2}')  # Output: num1: 1234.56789, num2: 9876.54321
```

- Precision can be specified as **`{variable:.precision}`**.
- For example: **`print(f'num1: {num1:.4}, num2: {num2:.4}')`** results in **`num1: 1234, num2: 9876`**.
- To control the number of decimal places in floats, use **`{variable:.precisionf}`**.

### Basic Printing (Less Ideal)

```python
num1 = 1234.56789
num2 = 9876.54321
print('num1:', num1, 'num2:', num2)  # Output: num1: 1234.56789 num2: 9876.54321
```

### Precision with **`.format()`** (Less Ideal)

```python
num1 = 1234.56789
num2 = 9876.54321
print('num1: {:.4}, num2: {:.4}'.format(num1, num2))  # Output: num1: 1234 num2: 9876
```

### **Joining Strings with `str.join()`**

The **`join()`** method combines a list of strings into a single string, using the calling string as a separator:

```python
separator = "-"
words = ["Hello", "world", "Python"]
result = separator.join(words)
print(result)  # Output: "Hello-world-Python"
```

# **Lists []**

---

### **List Creation**

Lists can contain mixed types in Python. For example:

```python
my_list = ['mario', 'luigi', 'bowser', 27]
```

### **List Operations**

- Accessing elements by index.
- Slicing with **`list[start:end]`**.
- Concatenating lists with **`+`**.
- Increasing list size with **`.append()`**.
- Decreasing list size with **`.pop()`**.
- Removing specific elements with **`.remove(element)`** or **`del list[index]`**.

### **Lists Within Lists**

You can nest lists within lists.

```python
nested_list = [['mario', 'luigi', 'bowser', 27], [1, 2, 3, 5, 8, 13, 21, 34, 55, 89], [1, 2, 3, 4]]
```

### List Comprehensions

1. **Basic List Comprehension**:
    
    ```python
    numbers = [1, 2, 3, 4, 5]
    squared = [x ** 2 for x in numbers]
    ```
    
    - Creates a new list **`squared`** by squaring each element in **`numbers`**.
2. **List Comprehension with Condition**:
    
    ```python
    numbers = [1, 2, 3, 4, 5]
    even_squared = [x ** 2 for x in numbers if x % 2 == 0]
    ```
    
    - Creates a new list **`even_squared`** with squared values of even numbers from **`numbers`**.
3. **Nested List Comprehension**:
    
    ```python
    matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    flattened = [x for row in matrix for x in row]
    ```
    
    - Creates a flattened list **`flattened`** by iterating through a nested list **`matrix`**.
4. **Dictionary Comprehension**:
    
    ```python
    names = ['Alice', 'Bob', 'Charlie']
    name_lengths = {name: len(name) for name in names}
    ```
    
    - Creates a dictionary **`name_lengths`** where keys are names, and values are their lengths.
5. **Set Comprehension**:
    
    ```python
    numbers = [1, 2, 3, 4, 5, 5, 4]
    unique_numbers = {x for x in numbers}
    ```
    
    - Creates a set **`unique_numbers`** containing unique elements from **`numbers`**.

### **Using `map()` with a Function and an Iterable**

The **`map()`** function applies a given function to each item in an iterable (e.g., a list) and returns an iterable with the results. It takes two parameters:

1. The function to apply.
2. The iterable (e.g., list) to apply the function to.

Here's a brief example:

```python
# Define a function
def double(x):
    return x * 2

# Create a list of numbers
numbers = [1, 2, 3, 4, 5]

# Use map() to apply the function to each item in the list
doubled_numbers = map(double, numbers)

# Convert the result to a list (optional)
doubled_numbers_list = list(doubled_numbers)

print(doubled_numbers_list)  # Output: [2, 4, 6, 8, 10]
```

In this example, **`map(double, numbers)`** applies the **`double`** function to each element in the **`numbers`** list, resulting in an iterable containing the doubled values.

### **Using `filter()` to Filter an Iterable**

The **`filter()`** function in Python filters an iterable (e.g., a list) based on a specified condition, returning a new iterable containing only the elements that meet the condition. It takes two parameters:

1. The function that defines the condition.
2. The iterable to filter.

Here's a concise example:

```python
# Define a function to check if a number is even
def is_even(x):
    return x % 2 == 0

# Create a list of numbers
numbers = [1, 2, 3, 4, 5, 6]

# Use filter() to keep only even numbers in the list
even_numbers = filter(is_even, numbers)

# Convert the result to a list (optional)
even_numbers_list = list(even_numbers)

print(even_numbers_list)  # Output: [2, 4, 6]
```

In this example, **`filter(is_even, numbers)`** applies the **`is_even`** function to each element in the **`numbers`** list, returning an iterable containing only the even numbers.

# Dictionaries {}

---

- **Defining a Dictionary**:
    
    ```python
    # DEFINE WITH CURLY BRACES!!!!
    my_dict = {"key1": "value1", "key2": "value2"}
    ```
    
- **Accessing Values**:
    
    ```python
    value = my_dict["key1"]
    ```
    
- **Removing Items**:
    
    ```python
    del my_dict["key1"]  # Removing a specific item
    my_dict.clear()  # Clearing the entire dictionary
    ```
    
- **Checking Key Existence**:
    
    ```python
    if "key1" in my_dict:
        # Key exists
    ```
    
- **Dictionary Iteration**:
    
    ```python
    for key, value in my_dict.items():
        print(key, value)
    ```
    
- **************Accessing Only Keys or Only Values as a List**************
    
    ```python
    keys_list = list(my_dict.keys())
    print(f'There are {keys_list.count('keyName')} instances of keyName')
    values_List = list(my_dict.values())
    ```
    

# **Standard Input**

---

### **Input from User**

Standard input (**`input()`**) returns user input as a string.

```python
username = input('Enter your name: ')
```

### **Printing**

- Use **`print()`** to display output.
- Commas add spaces between printed elements.
- Concatenate strings for custom formatting.

### **Casting**

You can convert a string to an integer using **`int(str)`**.

```python
radius = int(input('Enter a readius: '))
```

# **If Statements**

---

### **Conditional Statements**

- Use **`if`**, **`elif`**, and **`else`** for conditional logic.
- Logical operators **`and`** and **`or`** can be used in conditions.

## **For Loops**

### **Basic For Loops**

```python
for item in iterable:
    # Code to be executed for each item
```

### **For Loops with `range()`**

`stop` is non-inclusive

```python
for i in range(start, stop, step):
    # Code to be executed for each value of 'i'
```

Iterating through indexes a list

```python
for element in range(len(list)):
    # Code to be executed for each element in list
```

### **For Loops with `zip()`**

```python
for item1, item2 in zip(iterable1, iterable2):
    # Code to access 'item1' and 'item2'
```

### **For Loops with a Dictionary**

- Iterating over keys:

```python
for key in dictionary:
    # Code to access 'key'
```

- Iterating over values:

```python
for value in dictionary.values():
    # Code to access 'value'
```

- Iterating over key-value pairs:

```python
for key, value in dictionary.items():
    # Code to access 'key' and 'value'
```

- Example:

```python
student_scores = {"Alice": 90, "Bob": 85, "Charlie": 88}

# Iterating over keys
for name in student_scores:
    print(name)

# Iterating over values
for score in student_scores.values():
    print(score)

# Iterating over key-value pairs
for name, score in student_scores.items():
    print(f"{name}: {score}")
```

# **While Loops**

---

### **Basic While Loop**

A while loop in Python repeatedly executes a block of code as long as a specified condition is **`True`**.

```python
while condition:
    # Code to be executed as long as 'condition' is True
```

Example:

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

### **Break and Continue**

- You can use the **`break`** statement to exit a while loop prematurely.
- The **`continue`** statement can be used to skip the rest of the current iteration and continue to the next one.

Example:

```python
while True:
    user_input = input("Enter 'q' to quit: ")
    if user_input == 'q':
        break
    print("You entered:", user_input)
```

# **Functions**

---

### **Function Definition**

```python
def function_name(parameter1, parameter2):
    # Function bod
```

### **Default Parameters**

- Set default values for parameters.

```python
def greet(name, age=30):
    # Function body
```

### **Keyword Arguments**

- Use parameter names to specify values.

```python
greet(age=25, name="Alice")
```

### **Docstrings**

- Include a docstring to describe the function.

```python
def add(a, b):
    """
    This function adds two numbers.
    """
    return a + b
```

### **Lambda Functions**

Lambda functions, also known as anonymous functions, are concise, one-line functions defined using the **`lambda`** keyword. They are typically used for simple, short operations.

**Syntax:**

```python
lambda arguments: expression 
```

Example:

```python
double = lambda x: x * 2
result = double(5)  # result is 10
```

### **Decorators in Python**

Decorators in Python are **functions that modify the behavior of other functions or methods**. They are often used to add functionality or perform preprocessing to existing functions.

**Syntax:**

```python
@decorator_function
def some_function():
    # Function code here
```

Example:

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```

# **Sets**

---

### **SETS DO NOT INCLUDE DUPLICATES**

**Sets DO NOT preserve order (careful when casting!!)**

- **Defining a Set**:
    
    ```python
    my_set = {1, 2, 3}
    ```
    
- **Adding and Removing Elements**:
    
    ```python
    my_set.add(4)        # Adding an element
    my_set.remove(2)     # Removing an element
    ```
    
- **Set Operations**:
    - **Union**: Combines two sets, preserving unique values from both sets.
        
        ```python
        union_set = set1 | set2
        ```
        
    - **Intersection**: Returns the common elements between two sets.
        
        ```python
        intersection_set = set1 & set2
        ```
        
    - **Difference**: Returns elements in the first set but not in the second set.
        
        ```python
        difference_set = set1 - set2
        ```
        
- **Checking for Existence**:
    
    ```python
    if 3 in my_set:
        # Element exists in the set
    ```
    
- **Set Iteration**:
    
    ```python
    for item in my_set:
        print(item)
    ```
    
    # Classes
    
    ---
    
    - **Defining a Class**:
        
        ```python
        class MyClass:
            class_attr = 42  # Class-level attribute
        
            def __init__(self, param1, param2):
                self.param1 = param1
                self.param2 = param2
        
            def instance_method(self):
                # Instance method can access instance attributes
                return f"Instance method: {self.param1}, {self.param2}"
        
            @classmethod
            def class_method(cls):
                # Class method can access class attributes
                return f"Class method: {cls.class_attr}"
        
        		@staticmethod
            def static_method():
                # Static method doesn't access instance or class attributes
                return "Static method: No access to attributes"
        ```
        
    - **`__init__` Method**:
        - The **`__init__`** method initializes object attributes.
        - It always takes **`self`** as its first parameter to refer to the instance.
        - You can set instance attributes using **`self`**.
        - **Instance methods (that receive `self` as a parameter) cannot be called on the class**
    - **Naming Conventions**:
        - Class names are typically in CamelCase (e.g., **`MyClass`**).
        - Method and attribute names are in lowercase with underscores (e.g., **`my_method`**, **`my_attribute`**).
    - **Class-Level Attributes and Methods**:
        - Class attributes are shared among all instances.
        - Class methods are defined using **`@classmethod`** decorator and can access class-level attributes.
        - **Class methods can be called on the class or on an instance of the class**
    - **Static Methods**:
        - Static methods are defined using **`@staticmethod`** decorator.
        - They don't access instance or class attributes.
    - **Example**:
        
        ```python
        obj1 = MyClass("value1", "value2")
        obj2 = MyClass("value3", "value4")
        
        print(obj1.instance_method())  # Output: "Instance method: value1, value2"
        print(MyClass.class_method())  # Output: "Class method: 42"
        print(MyClass.static_method())  # Output: "Static method: No access to attributes"
        ```
        
        # Modules and Packages
        
        ---
        
        - **Modules**:
            - A module is a Python file containing reusable code.
            - Create a module by saving Python code in a **`.py`** file.
            - Import a module using **`import module_name`**.
            - Access module functions and variables using **`module_name.function_name`** or **`module_name.variable_name`**.
        - **Packages**:
            - A package is a **directory** containing multiple related modules.
            - Create a package by organizing modules in a directory with an **`__init__.py`** file (**this can be EMPTY**. This signifies that the directory is a package, but it doesn't define any special initialization actions.).
            - Import a module from a package using **`import package_name.module_name`**.
        - **Importing**:
            - Import specific functions or variables using **`from module_name import function_name`**.
            - Rename imported modules or functions using **`import module_name as alias`**.
            - Import all functions and variables using **`from module_name import *`** (not recommended for large modules).
        
        **Example**:
        
        ```python
        pythonCopy code
        # Importing a module
        import math
        
        # Using module functions
        print(math.sqrt(16))  # Output: 4.0
        
        # Importing specific functions
        from random import randint
        print(randint(1, 10))
        
        # Renaming imported module
        import datetime as dt
        print(dt.date.today())
        
        # Importing from a package
        from mypackage import mymodule
        print(mymodule.my_function())
        
        # Importing everything (not recommended)
        from mymodule import *
        
        ```
        
        # File I/O
        
        ---
        
        **Opening a File:**
        
        To open a file, you can use the **`open()`** function. It takes two main parameters: the file name (including the path) and the mode (read, write, append, etc.).
        
        ```python
        # Opening a file in read mode
        try:
            file = open("example.txt", "r")
            # File operations here
        except FileNotFoundError:
            print("The file does not exist.")
        except IOError:
            print("An I/O error occurred.")
        finally:
            file.close()  # Ensure the file is always closed, even if an exception occurs
        ```
        
        The most common way to open a file is using the **`open()`** function with various modes:
        
        - **`'r'`**: Read (default mode). Opens the file for reading.
        - **`'w'`**: Write. Opens the file for writing (creates a new file if it doesn't exist, truncates if it does).
        - **`'a'`**: Append. Opens the file for writing (creates a new file if it doesn't exist) and appends data to it.
        - **`'x'`**: Exclusive creation. Creates a new file and opens it for writing. If the file already exists, an error is raised.
        - **`'b'`**: Binary mode. Reads or writes the file in binary mode (e.g., **`'rb'`**, **`'wb'`**).
        - **`'t'`**: Text mode (default). Reads or writes the file as a text file (e.g., **`'rt'`**, **`'wt'`**).
        - **`'+'`**: Read and write. Allows both reading and writing (e.g., **`'r+'`**, **`'w+'`**).
        
        **Reading from a File:**
        
        You can use various methods to read data from a file. The most common method is **`read()`**, which reads the entire file or a specified number of bytes.
        
        ```python
        try:
            content = file.read()  # Reads the entire file
        except FileNotFoundError:
            print("The file does not exist.")
        except IOError:
            print("An I/O error occurred.")
        ```
        
        **Writing to a File:**
        
        To write data to a file, open it in write or append mode and use the **`write()`** method.
        
        ```python
        try:
            file = open("example.txt", "w")
            file.write("Hello, world!")
        except FileNotFoundError:
            print("The file does not exist.")
        except IOError:
            print("An I/O error occurred.")
        finally:
            file.close()  # Always close the file after writing
        ```
        
        **File Cursor:**
        
        The file cursor keeps track of the current position in the file. When you read or write, the cursor moves accordingly. You can use the **`seek()`** method to change the cursor position.
        
        ```python
        try:
            file = open("example.txt", "r")
            file.seek(0)  # Move the cursor to the beginning of the file
            content = file.read()
        except FileNotFoundError:
            print("The file does not exist.")
        except IOError:
            print("An I/O error occurred.")
        finally:
            file.close()
        ```
        
        **Using `with` Statement:**
        
        The **`with`** statement is a cleaner way to work with files. It automatically closes the file when you're done, even if an error occurs.
        
        ```python
        try:
            with open("example.txt", "r") as file:
                content = file.read()
            # File is automatically closed when you exit the 'with' block
        except FileNotFoundError:
            print("The file does not exist.")
        except IOError:
            print("An I/O error occurred.")
        ```
        
        # Citations and Thank Yous
        
        ---
        
        These notes were made possible by this wonderful playlist on youtube (and some help formatting/paraphrasing by ChatGPT):
        
        [https://www.youtube.com/playlist?list=PL4cUxeGkcC9idu6GZ8EU_5B6WpKTdYZbK](https://www.youtube.com/playlist?list=PL4cUxeGkcC9idu6GZ8EU_5B6WpKTdYZbK)
