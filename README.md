Python for Visual Basic programmers
=========================

A Python introdunction for Visual Basic programmers.

![image](./images/cover.jpg "Cover")

##Introduction

Python is a widely used high level programming language, its elegant syntax allows you to clearly define application behaviour using fewer lines of code than would be required in other languages like VB.  It supports multiple programming paradigms including imperative, functional and object oriented styles.  So you can do pretty much everything in it.

As a Visual Basic programmer the first thing you need to resign yourself to is not having the form designer.  Python is programmed in text.  You could still write desktop applications with buttons and menus though but the form layout must be described in code.  That is not covered in this document though.  However programs written in Python often don’t even need a desktop interface at all, so read on.

So this introduction is intended help a Visual Basic programmer apply their existing programming knowledge and experience to the world of Python on the Raspberry Pi.  This is by no means an exhaustive guide to Python.  For comprehensive documentation please visit: http://docs.python.org/2.7/

##Choosing a programming environment

###Desktop

You may have a preferred programming environment (the program to write code in) however if you need advice I can recommend a nice one called Geany.

[![image](./images/geany.png)](http://www.geany.org/)

Raspbian does not come with Geany so you have to install it.
To do this open up LXTerminal and enter the command below. 

`sudo apt-get install geany`

After the installation has completed you should find Geany inside the `Programming` folder of the launcher menu.  To start a new Python program go **File > New (with Template) > main.py**

Geany populates this with some template text (a copyright statement) and some function blocks at the bottom but you can delete everything except the first line to start afresh.  That first line is important because it denotes the file as a Python program.  The cogs icon at the top is the familiar run button (F5) similar to how it is in Visual Basic.

Enter the following code and press the run button.

```python
print "hello world"
```

###Command line

If you prefer the command line you can easily create a Python program using `nano` or `vim`.  Nano is nice a terminal based text editor.  For example enter the following command.

`nano test.py`

Enter the following lines of code into the file.  The first line specifies that the file is a python program.

```python
#!/usr/bin/python
print "hello world"
```

Press `Ctrl – O` to save, `Ctrl – X` to quit.  Next mark the file as executable, and then you can run it.

```
chmod +x test.py
./test.py
```

You only need to use the `chmod` command once per Python file.  It will remain executable even if you make copies of it.

##Basic data types

Python supports a wide range of data types.  Look at the table below.  Notice how Visual Basic requires variables to be defined along with their type?  *Python does not*.

Data type | Visual Basic | Python 
--- | --- | ---
Integer number | `Dim count As Integer` | `count = 1`
Floating point number | `Dim distance As Double` | `distance = 2.5`
Boolean | `Dim active as Boolean` | `active = False`
String | `Dim name as String` | `name = "Dave"`

In Python simply placing the whole number 1 or the fraction 2.5 into a variable will make the difference between it being an Integer or a Float respectively.  Because of this you should always initialise (put data into) variables as you define them.

A # character in Python denotes a comment, text that will be ignored.

```python
#!/usr/bin/python
counter = 1     #Integer
distance = 2.5  #Floating point
active = False  #Boolean
name = "Dave"   #String

print counter
print distance
print active
print name
```

This should produce the following output.

```
1
2.5
False
Dave
```

##Indentation

Python does not use begin and end tags to group lines of code into functions, loops or if-statements.  It uses white space indentation only and this is rigidly enforced.  Compare the code below.

* Visual Basic:
  ```vb
  Dim count As Integer
  count = 1
  
  If count > 0 Then
  	MsgBox "Hello"
  End If
  ```
* Python:
  ```python
  #!/usr/bin/python
  count = 1
  
  if count > 0:
    print "Hello"
  ```

Notice the colon in the Python code after the if-statement.  This is mandatory and it can help to think of it as the then keyword in Visual Basic.

Programs like Geany help you with this indentation, pressing enter after the colon will automatically indent the cursor.  If you're using the command line though you'll need to ensure the indentation is correctly entered.

You can either use multiple space characters or a tab character.  Tab characters tend to be more reliable for this purpose.  If you prefer to use spaces then the number of spaces in the indentation can be variable as long as they remain constant in each code block.  Compare the examples below.

* This will work:
  ```python
  #!/usr/bin/python
  count = 1
  
  if count > 0:
      print "hello"
      print "good morning"
  else:
    print "goodbye"
    print "good night"
  ```
* This will produce an error:
  ```python
  #!/usr/bin/python
  count = 1
  
  if count > 0:
      print "hello"
      print "good morning"
  else:
      print "goodbye"
    print "good night"
  ```

Understanding the rules of indentation is fundamental to Python and can represent a stumbling block for pupils.  Pupils often do not understand what white space is and therefore need to be shown that spaces and tabs are real text characters but are just invisible.   They have a purpose and are saved along with text in a document file.  Perhaps ask them how the computer remembers where the white space is in a text file?

![image](./images/msword-paragraph.png "Microsft Word Paragraph Button")

It can also be helpful to do a quick exercise in Microsoft Word where some code is typed out and the paragraph toolbar button (above) is used to show the hidden characters.  Space characters then show as a dot and tab characters show as an arrow.

Below is an example of two nested if-statements in Visual Basic and Python for comparison.  Here I am using tab characters as a preference because the resulting code looks neater and more readable.

* Visual Basic:
  ```vb
  Dim count As Integer
  Dim active As Boolean
  
  count = 1
  active = False
  
  If count > 0 Then
  	If active Then
  		MsgBox "Hello"
  	End If
  End If
  ```
* Python:
  ```python
  #!/usr/bin/python
  count = 1
  active = False
  
  if count > 0:
  	if active:
  		print "Hello"
  ```

##Arithmetic operators
The usual range of arithmetic operators are present in Python.  Examples of their use are shown in the table below along with Visual Basic code for comparison.

Operator | Visual Basic | Python 
--- | --- | ---
Add | `c = a + b` | `c = a + b`
Subtract | `c = a - b` | `c = a - b`
Multiply | `c = a * b` | `c = a * b`
Divide | `c = a / b` | `c = a / b`<br/>`c = a // b #Floor`
Modulus division | `c = a Mod b`	| `c = a % b`
Exponent | `c = a ^ b` |	`c = a ** b`

**Note**: In Python the division operator `/` will actually do a floor division if the variables being divided are both integers.  So whole numbers `10 / 3` gives `3` whereas floating point `10.0 / 3.0` gives `3.33` recurring.  You can also force floor division using the `//` operator if needed.

##Comparison operators

Again the usual range of comparison operators are found in Python, examples are shown in the table below.  Notice that both `<>` and `!=` can be used to test for inequality in Python and that equality uses the double equal `==` sign.

* Visual Basic:
  ```vb
  If a = b Then 'Equality
  	MsgBox "a is equal to b"
  End If
  
  If a <> b Then 'Inequality
  	MsgBox "a not equal to b"
  End If
  
  If a > b Then 'Greater
  	MsgBox "a greater than b"
  End If
  
  If a < b Then 'Less
  	MsgBox "a less than b"
  End If
  
  If a >= b Then 'Greater or equal
  	MsgBox "a greater or equal to b"
  End If
  
  If a <= b Then 'Less or equal
  	MsgBox "a less than or equal to b"
  End If
  ```
* Python:
  ```python
  #!/usr/bin/python
  if a == b: #Equality
  	print "a is equal to b"
  
  if a != b: #Inequality
  	print "a not equal to b"
  
  if a <> b: #Inequality
  	print "a not equal to b"
  	
  if a > b: #Greater
  	print "a greater than b"
  
  if a < b: #Less
  	print "a less than b"
  
  if a >= b: #Greater or equal
  	print "a greater or equal to b"
  	
  if a <= b: #Less or equal
  	print "a less than or equal to b"
  ```

##While loops

The Python while loop is quite like the "do while" loop in Visual Basic.

* Visual Basic:
  ```vb
  Dim counter As Integer
  counter = 1
  
  Do While counter <= 10
  	MsgBox counter
  	counter = counter + 1
  Loop
  ```
* Python:
  ```python
  #!/usr/bin/python
  counter = 1
  
  while counter <= 10:
  	print counter
  	counter = counter + 1
  ```

Execution does not enter the loop unless the while condition is met.  If the counter variable in the example above was already set to 11 then the entire loop would be skipped.

##For loops

The for loop in Python is extremely versatile and can be used to iterate over all manner of data such as lists (arrays), strings and dictionary objects.  There is no equivalent of the standard Visual Basic for loop in Python, there is only an equivalent of the *for each* loop.

Below is an example of a simple count from 1 to 3.  In Visual Basic the standard for loop is used.  In Python though we have to cheat a bit and create a list of numbers to iterate over.

* Visual Basic:
  ```vb
  Dim i As Integer
  
  For i = 1 To 3
  	MsgBox i
  Next i
  ```
* Python:
  ```python
  #!/usr/bin/python
  lst = range(1,4)
  for i in lst:
  	print i

  ```

Notice the use of the `in` keyword on the Python side.  The variable `lst` is actually a list containing the integers 1 to 3.  It's created by the range function by passing in the number to start from and the number to stop at (so stopping at 4 leaves 3 as the final number).

A more accurate comparison would be this code below.

* Visual Basic:
  ```vb
  Dim col As Collection
  Set col = New Collection
  
  col.Add 1
  col.Add 2
  col.Add 3
  
  For Each num In col
  	MsgBox num
  Next num
  ```
* Python:
  ```python
  #!/usr/bin/python
  lst = range(1,4)
  for num in lst:
  	print num
  
  #A shorter way to do the same
  for num in range(1,4):
  	print num
  ```

##Collections and arrays

In Python *lists* are somewhat similar to Collections in Visual Basic.  They have a number of built in functions to allow you to manipulate them.

* Visual Basic:
  ```vb
  Dim col As Collection
  Set col = New Collection
  
  col.Add "Cat"
  col.Add "Dog"
  col.Add "Rabbit"
  
  col.Remove 1
  
  MsgBox col.count
  ```
* Python:
  ```python
  #!/usr/bin/python
  lst = [] #An empty list
  
  lst.append("Cat")
  lst.append("Dog")
  lst.append("Rabbit")
  
  lst.remove("Cat")
  
  print len(lst)
  ```

Python lists can also be initialised with data on a single line of code in a similar manner to Visual Basic variant arrays.  The code below on the Python side will produce an identical list to the example above which was built using the append method.  Either way is valid, it’s just down to personal preference.

* Visual Basic:
  ```vb
  Dim vArray As Variant
  vArray = Array("Cat", "Dog", "Rabbit")
  
  MsgBox vArray(0)
  MsgBox vArray(1)
  ```
* Python:
  ```python
  #!/usr/bin/python
  lst = ["Cat", "Dog", "Rabbit"]
  
  print lst[0]
  print lst[1]
  ```

Notice the use of square brackets on the Python side.  Square brackets `[n]` are used to both define and index Python lists whereas curved brackets `(n)` are used in Visual Basic.

##Functions

Function blocks in Python are actually simpler than in Visual Basic.  In VB you have two types, `Sub` and `Function`, along with two modes of parameter, `ByVal` and `ByRef`.  In Python there is only one way to define a function which is the `def` keyword, parameters are always passed by reference and they are not typed.

Below is a comparison between a `Sub` function in Visual Basic (a function where there is no return value) and the equivalent Python code.

* Visual Basic:
  ```vb
  Sub PrintMe(ByRef s As String)
    MsgBox s
  End Sub
  
  PrintMe "first time"
  PrintMe "second time"
  ```
* Python:
  ```python
  #!/usr/bin/python
  def printme(s):
    print s
  
  printme("first time")
  printme("second time")
  ```

When a value needs to be returned in Visual Basic the `Function` keyword is used instead of `Sub`.  In Python there is no difference in how you define a function.  In VB the return value is set by assigning to the function name, `Sum = a + b`, whereas the `return` command is simply used to do this in Python, `return a + b`.  Compare the code below.

* Visual Basic:
  ```vb
  Function Sum(ByRef a As Integer, ByRef b As Integer) As Integer
      Sum = a + b
  End Function
  
  MsgBox Sum(5, 10)
  MsgBox Sum(10, 20)
  ```
* Python:
  ```python
  #!/usr/bin/python
  def sum(a, b):
  	return a + b
  
  print sum(5, 10)
  print sum(10, 20)
  ```

Optional function parameters are also possible in Python in the same way as Visual Basic.  In VB the `Optional` keyword is used and a default value is supplied (`= 0`).  In Python only the default value is required to make the parameter optional.

* Visual Basic:
  ```vb
  Sub ShowInfo(ByRef name As String, Optional ByRef age As Integer = 0)
  	MsgBox name
  	If age > 0 Then
  		MsgBox age
  	End If
  End Sub
  
  ShowInfo "John"
  ShowInfo "John", 30
  ```
* Python:
  ```python
  #!/usr/bin/python
  def showinfo(name, age = 0):
  	print name
  	if age > 0:
  		print age
  
  showinfo("John")
  showinfo("John", 30)
  ```

##Error handling

In Python runtime errors are called *exceptions*.  Python exception handling is actually a lot more sophisticated than the error handling in Visual Basic.  In VB the `On Error GoTo Label` statement is used along with an `Exit` to stop execution from going past said label.  Python uses a `try` block with one or more `except` clauses to test for different kinds of error.  The `else` clause runs if no exception occurs.  The `finally` block will always run regardless of what errors occur, ideal for closing files.

* Visual Basic:
  ```vb
  On Error GoTo ErrLabel
  
  Dim fso As New FileSystemObject
  Dim f As TextStream
  
  Set f = fso.CreateTextFile("test.txt")
  
  f.Write("Test Data")
  f.Close
  
  Exit Sub/Function
  
  ErrLabel:
  f.Close
  MsgBox "Error:" & Err.Description 
  ```
* Python:
  ```python
  #!/usr/bin/python
  try:
  	f = open("test.txt", "w")
  	f.write("Test Data")
  except IOError as e:
  	print "IO error:", e
  except:
  	print "unknown error"
  else:
  	print "success"
  finally:
  	f.close()

  ```

##Module and Class files

In Visual Basic modules and classes, `.mod` and `.cls`, are clearly separated out by the tree view of the development environment.  They represent separate files that contain code.  Module files hold one or more utility functions and class files contain the definition of a single OO object.

In Python there is no direct equivalent of this structure since all Python files have the `.py` extension.  It is possible to organise your code into numerous files and access them all from one place though.  This is done using the `from` keyword.

Consider the example below.  The file `mymodule.py` contains one function called `getanimals`.

```python
#!/usr/bin/python

def getanimals():
	lst = [] #An empty list
	lst.append("Cat")
	lst.append("Dog")
	lst.append("Rabbit")
	return lst
```

If you have multiple files the convention in Python is to name the entry point of the program (the file to be executed) `main.py`.  In main we want to access the `getanimals` function which is in `mymodule.py`.   The `from <file> import *` syntax is used.  Notice that the `.py` is not required here.

```python
#!/usr/bin/python

from mymodule import *

for animal in getanimals():
	print animal
```

Note that you will see `.pyc` files appearing with the same file name as the imported files (such as `mymodule.pyc`).  This is a Python byte code file and is essentially a compiled version of the source code.

##Object oriented programming

Python has excellent object oriented programming capabilities.  Classes also live in `.py` files in the same way as the module example above (and can be imported in the same way).  However their syntax structure is quite different to how it works in Visual Basic.  Below is a comparison between two *person* classes.

**Visual Basic** `clsPerson.cls`
```vb
Private m_name As String

Private Sub Class_Initialize()
	'Start up code here if needed
	m_name = ""
End Sub

Public Property Let Name(value As String)
	m_name = value
End Property

Public Property Get Name() As String
	Name = m_name
End Property

Public Sub Display()
	MsgBox Me.Name
End Sub
```

In VB the `Me` keyword can be used to access the current object or form properties.  Notice in the `Display` method where it is used above.

The following VB code would then be used to create an instance of the person class.

```vb
Dim obj As New clsPerson
obj.Name = "David"
obj.Display
```

In Python a class first needs to be defined with the class statement followed by a name, see the example below.  The first function `__init__` is the same as `Class_Initialize` in Visual Basic.  It runs when a new instance of the class is created in memory.  Notice the `self` statement, this is equivalent to the Visual Basic `Me` keyword and allows you to access properties of the current object.

When you define functions inside a class the `self` object must always be specified as the first parameter.  You don't have to explicitly specify it when calling the functions though Python does this behind the scenes for you.

There is also no concept of `Public` or `Private` class members in Python.  Everything is public and that means that the `setName` and `getName` functions below are redundant.  They are just there for comparisons to the Visual Basic code. 

**Python** `person.py`
```python
#!/usr/bin/python
class person:
	def __init__(self):
		#Start up code here if needed
		self.name = ""

	def setName(self, value):
		self.name = value

	def getName(self):
		return self.name

	def display(self):
		print self.name
```

So instead of having a private variable `m_name` with public get and set functions you can simply just define a variable as a member of self, `self.name = ""`, and it will then be publically accessible outside of the object.

```python
#!/usr/bin/python

from person import *

obj = person()
obj.name = "David" #or also; obj.setName("David")
obj.display()
```

If you have a situation where you want code to run as a property is being set or read then you will need to use a set or get function.  For example if you wanted to prevent negative numbers from being set on an *age* property for the person class.

* Visual Basic:
  ```vb
  Private m_age As Integer
  
  Public Property Let Age(value As Integer)
  	If value >= 0 Then
  		m_age = value
  	End If
  End Property
  ```
* Python:
  ```python
  #!/usr/bin/python
  def setAge(self, value):
  	if value >= 0:
  		self.age = value
  
  ```

Despite having the setAge function to constrain how `self.age` is set inside the class there is actually nothing to stop you from going `obj.age = -1` from outside the class and bypassing that logic.

However there is a convention in Python to indicate that a variable should not be touched from outside a class.  Using a double underscore, for example `self.__age`, is how this is done.  This generally warns anyone consuming your code to stay away from that variable despite the fact that they're not prevented from using it.

##Libraries and References (DLLs)

![image](./images/vba-references.png "VB Project References")

In Visual Basic its common practise to access pre made code from dynamic link libraries through the **Tools / References** menu option (see above).  DLL files are a Microsoft specific paradigm and are not used in Python on the Raspberry Pi because of the Linux based OS.  Instead Python comes with numerous code libraries (also written in the Python language) which you can just import into your program.  They cover almost everything you would ever need.

On the Raspberry Pi these libraries are found in the `/usr/lib/pyshared` and `/usr/lib directories`.  They can be easily accessed from your code using the `import` statement, you can have as many import statement in your program as is necessary.  Here are some examples.

```python
#!/usr/bin/python
import random
print random.randint(0,9) #Between 0 and 9
```

```python
#!/usr/bin/python
import datetime
a = datetime.datetime.now()
b = a + datetime.timedelta(1,0,0,0) #Add one whole day
print b
```

```python
#!/usr/bin/python
import math
x = 5
y = 10
hypotenuse = math.sqrt((x * x) + (y * y))
```

```python
#!/usr/bin/python
import MySQLdb
db = MySQLdb.connect("localhost", "appuser", "", "TestDB")
cursor = db.cursor()
cursor.execute("SELECT * FROM TABLE")
```

For a more extensive list of Python modules please visit this page: https://wiki.python.org/moin/UsefulModules
