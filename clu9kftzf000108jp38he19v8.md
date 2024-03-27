---
title: "🐍 Python 📘 for beginners"
datePublished: Wed Mar 27 2024 08:50:42 GMT+0000 (Coordinated Universal Time)
cuid: clu9kftzf000108jp38he19v8
slug: python-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711529312475/d5ffd887-a7d8-473c-ab35-84fdd1522bab.jpeg
tags: linux, aws, python, python3, devops, hashnode, python-beginner, shell-script

---

* **Introduction to Python**
    
* Welcome to the magical world of Python! Developed by Guido van Rossum and released in 1991, Python has become one of the most popular programming languages across various domains.
    
* **🚀 What is Python?**
    
* Python, created by Guido van Rossum and released in 1991, is a high-level programming language widely used for various purposes, including:
    
* 🌐 Web development (server-side)
    
* 🛠 Software development
    
* ➕ Mathematics
    
* 🖥 System scripting
    
* **📊 Data Types in Python**
    
* Python supports various data types to accommodate diverse programming needs:
    
* **int:** Stores integer values like 2, 3, 4, etc.
    
* **float:** Represents floating-point numbers such as 2.3, 3.4, 5.2, etc.
    
* **str:** Handles string data enclosed within double or single quotes, like "hello", "python", etc.
    
* **complex:** Manages complex numbers in the form of a + bj.
    
* **list:** Contains a collection of elements of different data types enclosed within square brackets \[\].
    
* **tuple:** Similar to lists but immutable, defined within parentheses ().
    
* **set:** Stores unique elements in curly braces {} without maintaining order.
    
* ---
    
* **📦 Check the Data Type**
    
* x = 5
    
* y = 3
    
* z = x + y
    
* print(type(z))
    
* x is assigned the value 5.
    
* y is assigned the value 3.
    
* z is assigned the sum of x and y.
    
* We then **print the data type of** z.
    
* **🔄Converting Data Types in Python**
    
* **Starting Data Type**: 📝 "123" (String)
    
* x = "123"
    
* print(type(x)) # Output: &lt;class 'str'&gt; 📝
    
* **Converted to**: 🔄 123 (Integer)
    
* y = int(x)
    
* print(type(y)) # Output: &lt;class 'int'&gt; 🔄
    
* **Converted to**: 🌊 123.0 (Float)
    
* z = float(y)
    
* print(type(z)) # Output: &lt;class 'float'&gt; 🌊
    
* ---
    
* **🧮 Variables**
    
* Variables in Python are used to store data values.
    
* x = 5
    
* y = 3
    
* z = x + y
    
* print(z)
    
* print the value of z, which is 8.
    
* **Multi-Variable:**
    
* x, y, z = "Orange", "Banana", "Cherry"
    
* print(x)
    
* print(y)
    
* print(z)
    
* three variables x, y, and z are assigned the string values "Orange", "Banana", and "Cherry" respectively.
    
* ---
    
* **🧮 Comments**
    
* Comments, denoted by **#** or enclosed within triple quotes (**''' '''**), enhance code readability and documentation.
    
* 📝 **User Input:**
    
* We prompt the user to enter their first value.
    
* The input is stored in the variable
    
* 💡 **Code**
    
* print("Enter first value")
    
* x = input()
    
* print("Enter last value")
    
* y = input()
    
* print(x, y, sep=' ') # 'sep' parameter adds a space between first and last value
    
* ---
    
* **🧮Line Change Function:**
    
* **\\n for Changing Lines**
    
* The \\n escape sequence in Python is used to create a new line.
    
* print("Hello\\n World!")
    
* Output:
    
* Hello
    
* World!
    
* **Printing with Multiple Line Spaces**
    
* it's set to '\\n', which means a new line.
    
* print("Hello", end='\\n\\n\\n\\n\\n\\n')
    
* print("World")
    
* Output:
    
* World
    
* **🧮Adding Space of Two Lines**
    
* input("Enter your name: ")
    
* print(end=' ') # Space equivalent to two lines
    
* input("Enter your age: ")
    
* **🧮Using \\t for Horizontal Space**
    
* The \\t escape sequence in Python is used to add horizontal space, simulating the space of two words.
    
* print("Hello\\t\\t World!")
    
* Output:
    
* Hello World!
    
* ---
    
* **Adding Two Numbers 🧮**
    
* 📌 **Input**: Prompt the user to enter two numbers.
    
* 🔄 **Conversion**: Convert the input strings to integers.
    
* ➕ **Addition**: Perform addition on the two numbers.
    
* 🖨️ **Output**: Display the result of the addition.
    
* x = int(input("Enter the first number: "))
    
* y = int(input("Enter the second number: "))
    
* print("Addition is:", x + y)
    
* **Number Systems:**
    
* **Decimal**: Base-10 system, digits range from 0 to 9.
    
* **Binary**: Base-2 system, digits are 0 and 1, prefixed with 0b.
    
* **Octal**: Base-8 system, digits are 0 to 7, prefixed with 0o.
    
* **Hexadecimal**: Base-16 system, digits are 0 to 9 and A to F, prefixed with 0x.
    
* **Conversion Examples:**
    
* Decimal to Binary: bin(435) returns **'0b110110011'.**
    
* Binary to Decimal: 0b110110011 equals **435**.
    
* Decimal to Octal: oct(435) returns **'0o663'**.
    
* Octal to Decimal: 0o663 equals **435.**
    
* Octal to Binary: 0o663 equals '**0b110110011**'.
    
* Decimal to Hexadecimal: hex(435) returns '**0x1b3**'.
    
* Hexadecimal to Decimal: 0x1b3 equals **435.**
    
* **Basic Mathematical Operations:**
    
* **Max**: Finds the maximum value in a list.
    
    * Example: max(\[12,55,88,66,45,894,155\]) returns **894.**
        
* **Min**: Finds the minimum value in a list.
    
    * Example: min(\[12,55,88,66,45,894,155\]) returns **12.**
        
* **Len**: Returns the length of a list.
    
    * Example: len(\[12,55,88,66,45,894,155\]) returns **7.**
        
* ---
    
* **Memory Optimization in Python 🧠**
    
* x = 5
    
* x ------&gt; 5
    
* id(x)
    
* **2185405977216**
    
* **Memory Optimization**:
    
* z = 5
    
* z ------&gt; 5
    
* id(z)
    
* **2185405977216** \----&gt;&gt; variable x & z id same
    
* **Comparison with Different Values**:
    
    * However, when assigning a different value to a new variable, Python allocates a new memory space for that value.
        
* y = 10
    
* y ------&gt; 10
    
* id(y)
    
* 140713063467736
    
* ---
    
* **🧮Comparing Equality in Python 🔄**
    
* **Equality Operators:**
    
* **\== :** Equal to
    
* \&gt;&gt;&gt; 10 == 20 ------------------------&gt;False
    
* \&gt;&gt;&gt; 10 == 10 ------------------------&gt;True
    
* **!= :** Not equal to
    
* \&gt;&gt;&gt; 10 != 20 ------------------------&gt;True
    
* \&gt;&gt;&gt; 10 != 10 ------------------------&gt;False
    
* **\&gt; :** Greater than
    
* \&gt;&gt;&gt; 12 &gt; 15 ----------------------&gt;False
    
* \&gt;&gt;&gt; 15 &gt; 12 -----------------------&gt;True
    
* **&lt; :** Less than
    
* \&gt;&gt;&gt; 20 &lt; 10 ------------------------&gt;False
    
* \&gt;&gt;&gt; 10 &lt; 20 -------------------------&gt;True
    
* **\&gt;= :** Greater than or equal to
    
* \&gt;&gt;&gt; 20 &gt;= 10 -----------------------&gt;True
    
* \&gt;&gt;&gt;10 &gt;= 10 ------------------------&gt;True
    
* \&gt;&gt;&gt; 10 &gt;= 20 ------------------------&gt;False
    
* **&lt;= :** Less than or equal to
    
* \&gt;&gt;&gt; 20 &lt;= 10 ----------------------&gt;False
    
* \&gt;&gt;&gt;10 &lt;= 10 -----------------------&gt;True
    
* \&gt;&gt;&gt; 10 &lt;= 20 ------------------------&gt;True
    

These operators return a Boolean value (True or False)

* ---
    
* **🔄 Control Flow Statements:**
    
* **Conditional Statements in Python 🚦**
    
* **Using If Statements (Yadi):** Executes a block of code based on a condition.
    
* x = 5
    
* y = 3
    
* \# Checking if x is greater than y
    
* if x &gt; y:
    
* print("x is greater than y")
    
* \# Checking if x is less than y
    
* if x &lt; y:
    
* print("x is less than y")
    
* **Using If...Else Statement:** Executes different blocks of code based on different conditions. always use last line of code
    
* x = -10
    
* \# Checking if x is positive or negative
    
* if x &gt; 0:
    
* print("Positive")
    
* else:
    
* print("Negative") # 📉
    
* **Using If...Elif...Else Statement:** Executes blocks of code based on multiple conditions.
    
* \# Taking input from user
    
* x = int(input("Enter a number: "))
    
* \# Checking if x is positive, negative, or zero
    
* if x &gt; 0:
    
* print(x, "is positive")
    
* elif x &lt; 0:
    
* print(x, "is negative")
    
* else:
    
* print(x, "is equal to zero")
    
* ---
    
* **Iterative statements 🚦:**
    
* **For Loop** : a for loop is used to iterate over sequences such as lists, tuples, string, etc.
    
* x="vaibhav"
    
* for v in x:
    
* print("hello")
    
* print("bye")
    
* ---
    
* **Range Function:**
    
* range(n) -----------------range(5) -------0,1,2,3,4 =&gt;5
    
* range(start, stop) -------range(5,7) -----5,6,7 =&gt;3
    
* range(start, stop, step) ---range(5,15,3) ---5,8,11,14 =&gt;4
    
* x="vaibhav"
    
* for m in range(5):
    
* print(x)
    
* ---
    
* **while loop :** while loop we can execute a set of statements as long as a condition is true.
    
* x=5
    
* while x&lt;15:
    
* print(x)
    
* x=x+1
    
* count = 1
    
* while count &lt;= 5:
    
* print(count)
    
* count += 1
    
* ---
    
* **And function:**
    
* x=float(input("enter first number x="))
    
* y=float(input("enter second number y="))
    
* z=float(input("enter third number z="))
    
* if x&gt;y and x&gt;z:
    
* print(x, "x is greater than y, z")
    
* elif y&gt;x and y&gt;z:
    
* print(y, "y is greater than x, z")
    
* elif z&gt;x and z&gt;y:
    
* print(z, "z is greater than x, y")
    
* else:
    
* print(x, y, z, "are equal")
    
* ---
    
* **Examples:**
    
* **step-1**
    
* k1=\[11,22,33,44,55,66,77,88\]
    
* L=len(k1)
    
* x=0
    
* while x&lt;L:
    
* print(x)
    
* x=x+1
    
* **step-2**
    
* k1=\[11,22,33,44,55,66,77,88\]
    
* x=0
    
* while x&lt;len(k1):
    
* print(x)
    
* x=x+1
    
* **step-3**
    
* k1=\[11,22,33,44,55,66,77,88\]
    
* x=0
    
* while x&lt;len(k1):
    
* print(k1\[x\])
    
* x=x+1
    

---

**Swapping:**

x=int(input("enter x value:"))

y=int(input("enter y value:"))

z=int(input("enter z value:"))

print("x=",x,"y=",y,"z=",z)

print("After Swapping")

x=y

y=z

z=x

print("x=",x,"y=",y,"z=",z)

---

**Multiplication:**

Multiplication is a basic arithmetic operation where one number is multiplied by another to get a result.

* 5×2=105×2=10
    
* This is straightforward multiplication.
    

**Modulo Operator (%):**

The modulo operator calculates the remainder of a division operation.

* 4%2=04%2=0:
    
    * Here, 4 divided by 2 equals 2 with no remainder, so the result is 0.
        
* 5%2=15%2=1:
    
    * Here, 5 divided by 2 equals 2 with a remainder of 1, so the result is 1.
        
* 7%3=17%3=1:
    
    * Here, 7 divided by 3 equals 2 with a remainder of 1, so the result is 1.
        

---

**List Operations:**

a = \[11, 22, 33, 44, 55\]

\# \[11\]\[22\]\[33\]\[44\]\[55\]

\# \[0\] \[1\] \[2\] \[3\] \[4\] # Indexing

print(a\[2\]) # Output: 33

print(a\[4\]) # Output: 55

**Option**:

x = \[11, 22, 33, 44, 55\]

x.append(88) # Appends 88 to the end of the list

x.clear() # Clears all elements from the list

del x # Deletes the list

x.sort() # Sorts the list in ascending order

x.reverse() # Reverses the order of elements in the list

x.remove(33) # Removes the first occurrence of the value 33 from the list

x.pop(2) # Removes and returns the element at index 2

x.insert(2, 77) # Inserts the value 77 at index 2

y = x.copy() # Copies the list x to y

x.extend(\[99, 66\]) # Extends the list x by appending elements from another list

print(x.count(11)) # Counts the number of occurrences of 11 in the list

x.insert(1, 56) # Inserts the value 56 at index 1

---

**slicing operator :** The slicing operator in Python is used to extract a portion of a sequence

syntax :

sequence\[start:end:step\]

h1 = \[1, 2, 5, 12, 86, 46 , 35, 14\]

g1 = h1\[2:4:1\]

print(g1) # Output: \[**5, 12**\]

g2 = h1\[2::2\]

print(g2) # Output: \[**5, 86, 35**\]

print(h1\[4:5:1\]) # Output: \[**86**\]

\# Reverse the list

print(h1\[-1::-1\]) # Output: \[**14, 35, 46, 86, 12, 5, 2, 1**\]

\# Extract the last element of the list

print(h1\[-1::1\]) # Output: \[**14**\]

---

**SET :**

* set start with {}
    
* duplicate data do not store in set
    
* set data do not indexing data \[0\]\[1\]\[2\]\[3\]\[4\]
    
* slicing operator do not support
    
* order does not maintain
    

\&gt;&gt;s1={11,22,33,44,55,22,44}

\&gt;&gt;s1

\&gt;&gt;{33, 22, 55, 11, 44}

***how to create empty set***

k1=set()

print(type(k1))

update :

s1={1,2,3,4,5}

s2={4,5,6,7}

s1.update(s2)

\&gt;&gt; s1

{1, 2, 3, 4, 5, 6, 7}

**Option**:

1\] add

2\] clear

3\] copy

4\] difference

5\] difference\_update

6\] intersection

7\] intersection\_update

8\] discard

9\] isdisjoint

10\] issubset

11\] issuperset

12\] pop

13\] remove

14\] symmetric\_difference

15\] symmetric\_difference\_update

16\] union

17\] update

---

**key-value :**

d1 = {"Name": "vaibhav", "Number": 123, "year": 2000}

print(type(d1)) # Output: &lt;**class 'dict**'&gt;

---

**Function: Python Functions is a block of statements that return the specific task. Increase Code Readability**

**Basic Function:**

def fun(x, y):

z = x + y

print("Addition of x + y:", z)

x = int(input("Enter the value of x: "))

y = int(input("Enter the value of y: "))

fun(x, y)

  
**Parameters Passing Function:**

def fun(p, q):

z = p + q

print("Addition of x + y:", z)

x = int(input("Enter the value of x: "))

y = int(input("Enter the value of y: "))

fun(x, y)

  
**Return Function:**

def fun(p, q):

z = p + q

return z

x = int(input("Enter the value of x: "))

y = int(input("Enter the value of y: "))

result = fun(x, y)

print("Addition is:", result)

**following 4 types of function arguments.**

**1\] Default argument**

def fun1(x, y):

z=x+y

print(z)

fun1(10,20)

&

def fun1(x,y,z=0):

z=x+y+z

print(z)

fun1(10,20)

fun1(10,20,30)

**2\] Keyword arguments (named arguments)**

def fun1(x,y,z=0):

t=x+y+z

print(x,y,z)

print(t)

fun1(y=10,z=20,x=30)

**3\] Positional arguments**

def nameAge(name, age):

print("Hi, I am", name)

print("My age is ", age)

print("Case-1:")

nameAge("Suraj", 27)

print("\\nCase-2:")

nameAge(27, "Suraj")

**4\] Arbitrary arguments (variable-length arguments *args and* \*kwargs)**

def fun1(\*g):

print(g) # data is truple form

t=list(g)

print(t)

fun1(10)

fun1(10,20,30,40)

fun1(10,20,30,40,50,60,70,80,90,100,110,120)

\# OR

def myFun(\*a):

for i in a:

print(i)

myFun('Hello', 'Welcome', 'to', 'GeeksforGeeks')