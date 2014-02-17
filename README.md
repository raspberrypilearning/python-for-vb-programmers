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
