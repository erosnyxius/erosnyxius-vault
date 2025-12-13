### Python Version Management - PyEnv
https://github.com/pyenv/pyenv

Installation For Linux
```bash
curl -fsSL https://pyenv.run | bash
```

Set Up Your Shell Environment 
```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
```

Set Up Your Shell Profile
```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo 'eval "$(pyenv init - bash)"' >> ~/.profile
```

Install Dependencies For Debian
```bash
sudo apt update; sudo apt install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl git \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

Install Stable Python Version For Global
```bash
pyenv install <version>
```

Before Activating Installed Version See Which Is By Default 
```bash
[iced@coffee ~]$ python --version
Python 3.13.7
```

Changing Global Python Version To PyEnv Installed Version
```bash
pyenv global <version>
```

Changing Python Version For Specific Folder/Project
```bash
pyenv local <version>
```

Changing Python Global Version To System Version
```bash
pyenv global system
```

### 📘 Virtual Environment 

```bash
python -m venv <PROJECT_NAME>

# If You Want Hide Folder
python -m venv .<PROJECT_NAME>

# Linux
source <PROJECT_NAME>/bin/activate

# Windows
cd <PROJECT_NAME>\Scripts\
activate 

# Check Virtual Environment
pip freeze

# Generate Requirements.txt 
pip freeze > requirements.txt

# Install Requirements.txt 
pip install -r requirements.txt

# After That Upgrdae pip !!
python -m pip install --upgrade pip (Linux)

# Extra .exe For Windows!
python.exe -m pip install --upgrade pip (Windows) 
```

**Python Environment in VS Code**

1.Install **"Python"** Extension 
2.`Python: Select Interpreter`
3.**Choose Your Python Environment**
Select Path Of Interpreters "python.exe" 
 
```python
# This Command Shows Where Is The "python.exe" !!
import sys
print(sys.executable)
```

Once the interpreter is selected:
* Now, **every time you press `Run` or `F5`**, VS Code uses **that interpreter** 

- Always AI Use করবো Concept বুঝার জন্য 
- যখন কোনো কিছু দরকার / করার জন্য Documentations দেখবো 
### 📘 Step 1 — Core Fundamentals

#### ` Basic Syntax Of Python `

```python
# যেহেতু Python Interpreted Language তাই এটার
# C++ এর মতো কোনো main() নেই

print('Learning Python Phase 1 — Fundamentals!\n')

# Print Pyramid Using Print Function
print('*') # String Can Multiply N Times!
print('*' * 2)
print('*' * 3)
print('*' * 4)
```

#### `Variables`

```python
# কোনো কিছু Store করার জন্য Variable Use করা হয় !
# লিখার ৩ টা নিয়ম -
# Camel Case: studentInfo
# Pascal Case: StudentInfo
# Snake Case: student_info

studentDepartment = 'CSE' # কোনো কিছু Assign করলে Variable Create হয় !
StudentBatch = 67
student_id = 202331067042

print('Bangladesh University\n'
      'Department:', studentDepartment, '\n'
      'Batch:', StudentBatch, '\n'
      'ID:', student_id)
```

#### `Data Types`

```python
# Data Types হচ্ছে যেগুলো আমরা Variable এ Store করি,
# এবং এটি নির্ধারণ করে যে Variable টি কোন ধরনের ডেটা আছে

# Basic ৩ ধরণের Data Types আছে !
# 1. Numbers(Integer, Float, Complex) 2. Strings 3. Boolean

# Integers (-∞ .., -2, -1, 0, 1, 2, ... ∞)

X = -2
Y = 3
print('Neg: ', type(X), '\nPos: ', type(Y), '\n')

# Float (দশমিক, ভগ্নাংশ - 56.8, 2/3)

X = 56.8
Y = 22/7
print('Dec: ', type(X), '\nFrac: ', type(Y), '\n')

# Complex (3 + 5j, এখানে 3 = real , 5j হলো imag , j হলো √-1)

Z = 3 + 5j
print('Comp: ', type(Z) , '\n')
print('Real :', Z.real)
print('Imag :', Z.imag)

# String (এমন এক ধরনের ডেটা যা যেকোনো কিছু সংরক্ষণ করতে পারে,
# কীবোর্ডে থাকা যেকোনো অক্ষর, সংখ্যা, চিহ্ন ইত্যাদি সব, ' ' অথবা " ")

FullName = 'Mahtabul Shourav'
print('Name: ', type(FullName))

# Boolean (True/1 অথবা False/0)

ManIsMortal = True
print('Man Is Mortal: ', type(ManIsMortal))
```

#### `Strings and String Methods`

```python
# Strings অন্য যেকোনো Data Type থেকে বেশি Space Use করে !
# কারন String এর সব Char তাদের Unicode Wise Store করে

Letter = 'A'
Emoji = '😂'

print('A Unicode: ', ord(Letter))
print('Haha Unicode: ', ord(Emoji))

# Unicode থেকে Character

print('Haha: ', chr(128514))


# String Indexing


#    Pos Index = 0  1  2  3  4  5  6  7  8  9
# "Bangladesh" = B  a  n  g  l  a  d  e  s  h


#    Neg Index = -10  -9  -8  -7  -6  -5  -4  -3  -2  -1
# "Bangladesh" =  B    a   n   g   l   a   d   e   s   h

Country = 'Bangladesh'

print('Pos Index:', Country[0] , Country[-10])

# String Slicing (String থেকে Slice নেয়া)
# Slice = [Start : Stop + 1: Steps]

# Bangladesh কে Slice করে Bangla

print('No Sliced: ', Country[::])

print('Slice 1: ', Country[0 : 6: 1])
print('Slice 1: ', Country[-10 : -4: 1])

print('Slice 2: ', Country[6:10:1])
print('Slice 2: ', Country[-4::1]) # 0 আসলে কিছু দিব না !
```

```python
# Some Usefull String Methods


```

#### `Type Conversion`

```python
# Type Conversion
# int()     float()     str()     bool()    complex()

# list()    tuple()     set()     dict()    পরে দেখবো !!
# এইগুলো সব Explicit Conversion

# String থেকে Integer
StringNum = '1234'

IntNum = int(StringNum)

print('Type: ', type(StringNum), StringNum)
print('Type: ', type(IntNum), IntNum)


# অন্য যেকোনো টা থেকে Boolean
# Falsy Values = False, 0, 0.0, "", '', [], () , {}
# এই 7 টা বাদে সবার জন্য True

# Multiple Declaration
A, B, C, D, E, F, G, H = False, 0, 0.0, "", '', [], () , {}

print(bool(H)) # সব গুলোর জন্য False আসবে, কারন ফাঁকা !!

# Implicit Conversion (যেগুলো Python Automatic Convert করে ফেলে)
A = 22
B = 7

print('PI: ', type(A/B), A/B)
```

#### `Input and Output`

```python
# Output = print()

# Raw String
Name = 'Shourav'
Age = 23

print('Name:', Name, 'Age:', Age)

# , → Automatically ' ' Add করে ফেলে শেষ এ !! 
# Always Python Documentation দেখবো কেন করে !! 

# Formatted String (এটা Use করবো)
# f' Text {Variable} '

print(f'Name: {Name} Age: {Age}')

# Input = input() Always Variable এ Store করবো
# না হলে Garbage Value Store হবে !
# InputVariable = input("Text") যা String হিসেবে Store করবে !!!

Name = input('Enter Your Name: ')
print(f'Name: {Name}')

# Type Change হলে Type Conversion Use করবো
# type(input("Text"))

Age = int(input('Enter Your Age: '))
print(f'Name: {Age}')


# print() → Automatically '\n' Add করে ফেলে শেষ এ !! 
# Always Python Documentation দেখবো কেন করে !! 

print('Hello', end =' ')
print('World', end =' ')
```

#### `Operators`

```python
# Operator হলো একটা Symbol যা Variable আর Values এর মধ্যে Operation করে
# যেমন - Arithmetic, Comparison, Logical and Assignment

# Arithmetic Operators (+, -, *, /, %, //, **)
# এইখানে // হলো Floor Division (integer)
# ** হলো Exponentiation (Power) যেখানে B = Base and P = Power (B ** P)

A = 100
B = 12

print(f'+: {A + B}')
print(f'-: {A - B}')
print(f'*: {A * B}')
print(f'/: {A / B}') # float
print(f'%: {A % B}')
print(f'//: {A // B}') # int
print(f'**: {A ** B}')


# BODMAS নিয়ম

# Brackets: আগে ( ), { } এর কাজ
# Orders: Power অথবা Root এর কাজ
# Division and Multiplication: From Left To Right.
# Addition and Subtraction: From Left To Right.

print(f'{(12-6)/3+2}') # 1. 12-6 = 6 2. 6/2 = 2 3. 2+2 = 4
```

```python
# Assignment Operator ( = )

myPoint = 12

myPoint = myPoint + 12

print(f'myPoint: {myPoint}')

# Compound Assignment Operator ( ArithmeticOperator= )

print('Compound Operators: ')

myPoint += 12
print(f'myPoint: {myPoint}')

myPoint -= 12
print(f'myPoint: {myPoint}')

myPoint *= 12
print(f'myPoint: {myPoint}')

myPoint /= 12
print(f'myPoint: {myPoint}')

myPoint %= 12
print(f'myPoint: {myPoint}')

myPoint //= 12
print(f'myPoint: {myPoint}')

myPoint **= 12
print(f'myPoint: {myPoint}')
```

```python
# Comparison Operators ( ==, !=, <, >, <=, >= )
# সব সময় True or False Return করবে !!

A = 100
B = 200

print(f'==: {A == B}')
print(f'!=: {A != B}')
print(f'<: {A < B}')
print(f'>: {A > B}')
print(f'<=: {A <= B}')
print(f'>=: {A >= B}')

# String এর মধ্যেও Apply করা যাবে But ASCII Value Wise হবে !!
print('Strign Compare:')

A = 'A'
B = 'B'

print(f'<: {A < B}') # A = 65
print(f'>: {A > B}') # B = 66
```

![LogicGate.png](data:image/png;base64,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)

Apply This Using Python Code!!

```python
# Logical Operators ( and, or, not )

# and = সব True হলে True হবে !
# or = যেকোনো একটা True হলেই True হবে
# not = যা থাকবে তার উল্টো হবে True <-> False

# (A and B)
# (C and (not D))
# (A and B)or (C and (not D))

# Multiple Variable Declaration
A, B, C, D = 1, 1, 1, 0 # Binary Values From Truth Table!

Y = ((A and B) or (C and (not D)))

print(f'Y = {Y}')
```

#### `Expressions`

```python
# Let's Solve Ax^2 + Bx + C Equations!

A = int(input('Enter A: '))
B = int(input('Enter B: '))
C = int(input('Enter C: '))

X = (-B + ((B*B - 4*A*C)**0.5)) / 2*A # Built-In Use না করে

print(f'Solution For X1 = {X}')


X = (-B - ((B*B - 4*A*C)**0.5)) / 2*A # Neg
print(f'Solution For X2 = {X}')

# X^2 - 5X + 6 = 0 Where, A = 1, B = -5, C = 6
```

#### `Control Flow`

```python
# If / Else এক বা একাধিক Conditions Check করার জন্য Use করবো !

# if Condition:
if 1:
    print('True') # Print True! Condition = True / 1


# if Condition:    else:
if 0:
    print('True')
else:
    print('False') # Print False! Condition = False / 0

# অনেকগুলো Condition Check করার জন্য elif Condition: !!

A = 'Arch'

if A == 'Arch':  # Bracket Use করবো দরকার হলে !!
    print('I use Arch btw!')
elif A == 'Debian':
    print('I use Debian btw!')
elif A == 'Fedora':
    print('I use Fedora btw!')
else:
    print('Maybe Others!')


# Let's Find Leap Year! Always Use Google না জানা থাকলে !!
# ( Year % 4 == 0 )  AND ( Year % 100 != 0 OR Year % 400 == 0 )

Y = 2028

if Y % 4 == 0 and Y % 100 != 0 or Y % 400 == 0:
    print('Leap Year!')
else:
    print('Normal Year..')
```

```python
# Match / Case এক বা একাধিক Specific Value Check করার জন্য Use করবো !

X = 'Banana'

match X: # match VaribaleName
    case 'Apple':
        print('Found Apple!') # case Value1:
    case 'Banana':
        print('Found Banana!') # case Value2:
    case 'Orange':
        print('Found Orange!') # case Value3:
    case _:
	    print('Found Nothing')
```

#### `Loops`

```python
# Python এ দুই ধরণের Loop আছে !
# For Loop কাজ করে Specific Number এর উপর
# While Loop কাজ করে Conditions এর উপর

# range(Start, Stop + থেকে 1 Step বেশি, Steps) আর in =  ভিতরে যাওয়া !!
# By Default Start = 0, Steps = 1

Numbers = range(1,11,1)

for i in Numbers:        # for idx in Variable:
    print(f'i: {i}')

print('Another One: ')

# যখন Specific Number নিয়ে কাজ করবো!
for j in range(2,21,2):        # for idx in range():
    print(f'j: {j}')


print('Loop From 16 To 1')

for x in range(16,0,-1): # Forward থাকলে + 1 or Reverse - 1
    print(f'x: {x}')


print('Loop From -3 To -18')

for x in range(-3,-19,-1):
    print(f'x: {x}')
```

```python
# For Loops For Strings

# Iterate দুইভাবে করা যায় !!
# 1. Index Values Use করে 2. Directly String Use করে

# 1. Index Values Use করে

# Length বের করতে হবে কারন For Loop কাজ করে Specific Number এর উপর!

# Length বের করার জন্য len() Use করবো !

Name = 'Learning Python!'

print('Method - 1')

for i in range(len(Name)): # By Default Start = 0, Steps = 1
    print(f'Index [{i}] = {Name[i]}')

print('\nMethod - 2')

# 2. Directly String Use করে

for char in Name:
    print(f'{char}')
```


```python
# Continue & Break Statements

# A ---------------------------- D  A থেকে D তে যাবো !
# A ------------ B                    Break পেলে ঐখানেই Stop করে দিব
# A ------- C[    ]------------- D  Continue পেলে মাঝের [ ] টুকু Skip করবো

print('Understanding Break')

for i in range(1,11):
    if i == 5:
        print('Break Applied')
        break           # এইখানেই শেষ !!

        print('ABCD')   # Loop Close হয়ে গেছে তাই কাজ করে নি !
    print(i)


print('\nUnderstanding Continue')


for i in range(1,11):
    if i == 5:
        print('Continue Applied')
        continue        # Continue পেলে Skip করে দিবে !!
        print('ABCD')   # আবার Loop Run হলো তাই কাজ করে নি !

    print(i)


# Break Run করলে Else Run করবে না, Break Run না করলে Else Run করবে!

print('\nBreak Vs Else')

for i in range(1,11):
    if i == 12:     # Range এর মধ্যে দিয়ে দেখবো !
        print('Break Applied')
        break
    print(i)
else:
    print('Break Not Applied')
```

```python
# While Loop কাজ করবে যতক্ষণ Condition True থাকবে !!

# Counter_Varibale দিব Condition এর জন্য !

Num = 1  # 1 To 30 !!

while Num <= 10:
    print(f'Num: {Num}')
    Num += 1 # Counter কে Increment / Decrement Must দিতে
             # হবে, না হলে Infinite Loop হবে !


# Number থেকে Digit আলাদা করা
Num = int(input('Enter Your Number: '))

while Num > 0:
    print(Num % 10)
    Num = Num // 10 # int লাগবে তাই !!
```

```python
# Number Guessing Game

import random

num = random.randint(1,10) # 1 থেকে 10 এর মধ্যে Limit!

guess = int(input('Guess Any Number: '))

print('Before While Loop!')

if num == guess:
    print('Your Guess Is Right!')
else:
    print('Your Guess Is Wrong!')


print('After Adding While Loop!')
# এখন এইটাকে 5 বার Try Add করার জন্য !

tries = 1 # Counter Condition এর জন্য !

while tries <= 5:
    print(f'Tries Left: {6 - tries}')

    guess = int(input('Guess Any Number: '))

    if num == guess:
        print('Your Guess Is Right!')
        tries += 1
        break

    elif num < guess:
        print('Go Little Lower!')
        tries += 1

    elif num > guess:
        print('Go Little Higher!')
        tries += 1

    else:
        print('Your Guess Is Wrong!')
        tries += 1
```

#### `Functions`

```python
# Function - 1. Built-In 2. User Defined

# 10 Industry Used Built-In Functions

# এইগুলো জানা হলো !
# len()
# range()

# পরে আরও জানবো !
# enumerate()
# zip()
# map()
# filter()
# open()
# sum()
# sorted()
# any()
# all()

# User Defined Function

# Function Define করা

def myFunction():
    print('Function Is Called!')

# Function Call করা, ইচ্ছা মতো

myFunction()


# Function With Parameters

def squreRoot(Num):  # Function যেটা Accept করে সেটা Parameters
    prevNum = Num
    Num = Num ** 0.5
    print(f'Square Roof Of {prevNum} Is {Num}')


squreRoot(49) # যেটা Parameters কে পাঠায় সেটা Arguments

# যে কয়টা Parameters সে কয়টা Arguments দিতে হবে !!

# 3 Types Of Arguments
# 1. Positional Arguments, Normallt যেটা Order Maintain করে
# 2. Keyword Arguments, Key = Value Use করে
# 3. Default Arguments, Parameter = Value Use করে


# 2. Keyword Arguments, Key = Value Use করে

def sayHello(Name,Age):
    print(f'Hi, {Name}! You\'re {Age} Year Old !')

sayHello(Age = 21, Name = 'Shourav') # আগে পরে কোনো Matter করে না


# 3. Default Arguments, Parameter = Value Use করে

def govtInfo(Name,City,Country = 'Bangladesh'):
    print(f'Name: {Name} \nCountry: {Country} \nCity: {City}')


govtInfo('Shourav','Dhaka')
```


```python
# Return Statement শুধু মাত্র Function এই Use করা যাবে !!!

def studentMarks(Mark):
    if Mark > 90:
        return 'Top Student'
    elif Mark < 90 and Mark > 80:
        return 'Good Student'
    else:
        return 'Avarage Student' # এইখানেই Code Exit হয়ে যাবে !!
        print('This Will Not Print!')


studentMarks(76) # যেইখানে Function Call হবে সেইখানে Value Return করবে !!

# Normally কিছু আসে নি! কারন Value Store করা হয় নি এর জন্য !!

returnedValue = studentMarks(76)

print(f'studentMarks(76) = {returnedValue}')
```

#### `String Literals`

```python
# String Literals

Name = 'Mahtabul'
Age = 21

StringLiterals = f'His name is {Name} and age is {Age}!'

print(StringLiterals)

# Function এর ক্ষেত্রে এইভাবে Use করবো

def myFunction(A,B):
    return f'The Sum Of {A} + {B}  = ', A + B

StringLiterals, ReturnValue = myFunction(12,98)

print(StringLiterals,ReturnValue)
```

#### `Pass Statement`

```python
# pass / ... = “Do Nothing” এটা add করা হয় Error Prevent
# বা পরে Code করার জন্য

for i in range(1,11):
    pass


for i in range(1,11):
    if i % 2 == 0:
        pass
    else:
        print(i)


def myFunction(A,B,C):
    ... 
```

#### `Recursion`

![1.PNG](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABJsAAAJaCAYAAACIk0Y2AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEE0AABBNAWeMAeAAALW2SURBVHhe7N1nuxPV//796zH86E2QXgSUJgKCgoCACkgRCx1FQAS7NAEBKYqggKIURRQEBFEQpDfpnb/PZ67jnO+xtmsmn2Rn751kT5L3jdeh7KyZJJMpa85Z5f/7v//7vwAAAAAAAADIBcImAAAAAAAA5AxhEwAAAAAAAHKGsAkAAAAAAAA5Q9gEAAAAAACAnCFsAgAAAAAAQM4QNgEAAAAAACBnCJsAAAAAAACQM4RNAAAAAAAAyBnCJgAAAAAAAOQMYRMAAAAAAAByhrAJAAAAAAAAOUPYBAAAAAAAgJwhbAIAAAAAAEDOEDYBAAAAAAAgZwibAAAAAAAAkDOETQAAAAAAAMgZwiYAAAAAAADkDGETAAAAAAAAcoawCQAAAAAAADlD2AQAAAAAAICcIWwCAAAAAABAzhA2AQAAAAAAIGcImwAAAAAAAJAzhE0AAAAAAADIGcImAAAAAAAA5AxhEwAAAAAAAHKGsAkAAAAAAAA5Q9gEAAAAAACAnCFsAgAAAAAAQM4QNgEAAAAAACBnCJsAAAAAAACQM4RNAAAAAAAAyBnCJgAAAAAAAOQMYRMAAAAAAAByhrAJAAAAAAAAOUPYBAAAAAAAgJwhbAIAAAAAAEDOEDYBAAAAAAAgZwibAAAAAAAAkDOETQAAAAAAAMgZwiYAAAAAAADkDGETAAAAAAAAcoawCQAAAAAAADlD2AQAAAAAAICcIWwCAAAAAABAzhA2AQAAAAAAIGcImwAAAAAAAJAzhE0AAAAAAADIGcImAAAAAAAA5AxhEwAARa5ly5ZBt27dggEDBgTdu3cP/22Vy4WGDRsGjRs3Dpo0aRI0a9YsaNGiRfDwww+H79mmTZugbdu2Qfv27YOOHTsGjzzySNClS5ega9eu4efTZ+vZs2fw+OOPB0888UTQt2/foF+/fkH//v2Dp556Khg4cGBo6NChwbBhw4IRI0YEI0eODEaPHh2MHTs2GD9+fPDyyy8Hr732WmjSpEnB1KlTgxkzZgRvvPFGMGvWrGDOnDnB22+/HcyfPz947733gg8++CD48MMPQx999FHw8ccfBwsXLgwWLVoULF68OLRkyZLgk08+CZYtWxYsX748+PTTT4MVK1aEVq5cGXz22WfB6tWrgzVr1gRr164NrVu3Lvjiiy+C9evXB19++WWwYcOG0MaNG4Ovv/462LRpU7B58+Zgy5YtwTfffBPaunVr8N133wXff/99sG3btmD79u2hHTt2BD/88EPw448/Brt27Qp++umnYPfu3RX0N722c+fOimW0vNb17bffhuvW++j99N76DPos+lz6jJ9//nnF59b3WLVqVcX303fV99b3d9tD22bBggXh9tJ20zbUttQ2feutt8LtrG0+bdq08Dd45ZVXwt9mzJgx4e+l302/n35L/a76jXv37h3+/toXtG9oP9F+07Rp03CfsvY1AABQvAibAAAoMrph102/Aoj/9//+H1Aybt26FZw9ezY4fPhwGKrNnDkzDKes4wAAACQXYRMAAEWiV69eYUsW6yYdKGUKn9TCzTouAABA8hA2AQBQBNSFyboJB8qJuhUqdLWOEQAAkByETQAAJJzGBbJuvIFypTGrOnXqZB4vAACg9hE2AQCQYBr42brZlitXroQDUWuwbA22rQG5NXC3tZ5caNSoUWRw8ObNm4cDhGtw8FatWkUGCO/QoUMYBnTu3LlikPDHHnssHCS6R48eaQcK1yDnTz/9dMVg4dUxePDgcIDq5557LhywWgNXawBrDWQ9ceLEYMqUKeEA1xoPaPbs2eGA4u+88044CDZS+QODv/766xUDg7/66qvBSy+9VDEwuLa3tru2v/W7ZGPIkCHhujVo+8mTJ8393tH+rwHIrX0VAADULsImAAASSjOFWTfZmrmM8WtQDhROKuy6ePGieSyIQi9rWQAAUHsImwAASCC1HonfVGumLk0rb5UHSt0bb7yRckw4alllLQMAAGoHYRMAAAnz6KOPptxMq8uQupxZ5YFy8eSTT5qtnK5evRq0a9fOXAYAABQeYRMAAAnz66+/ptxMazwbqyxQbjQu2Pnz51OOkY0bN5rlAQBA4RE2AQCQIJrWPX4TPWfOHLMsUK569+4d3Lt3L3KcPHjwIOjYsaNZHgAAFBZhEwAACbJu3brIDfSxY8eCOnXqmGWBcqZZGP1jRdasWWOWBQAAhUXYBABAQtStWze4ceNG5OZZ08BbZQH8X7Br167I8aLWTupmZ5UFAACFQ9gEAEBC9OzZM3LjrEHB69evb5YF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)

```python
# Recursion হলো একটা Function যা নিজেকে Call
# করতে পারে সাথে Base Case Exit করতে পারে  !!
# এই Method কে বলা হয় Recursive !!


# 1 থেকে 10 পর্যন্ত Print Using Recursion

# func printNumbers(L,U)
#      Base Case -> True -> L > U হয় তাহলে Exit/Return
#      Base Case -> False -> print(L)
#                   আবার printNumbers(L + 1, U)

def printNumbers(L,U):
    if(L > U):
        print('Head Recursion Ended!\n')
        return
    print(f'Print({L}) = {L}')
    print(f'Calling printNumbers({L+1, U})') # For Visualize
    printNumbers(L + 1, U)

printNumbers(1,10) # Head Recursion



def printNumbers(L,U):
    if(L > U):
        print('Tail Recursion Ended!\n')
        return
    print(f'Calling printNumbers({L+1, U})') # For Visualize
    printNumbers(L + 1, U)
    print(f'Print({L}) = {L}')

printNumbers(1,10) # Tail Recursion
```

#### `Scope & Lifetime`

```python
# যখন কোনো Variable Declare করা হয় তখন সেটা Global Scope
fruit = 'Apple' # Global Scope এই File এর সব জায়গায় Available!

def smallContainer(fruit):  # Function এর নিজের Local Scope থাকবে !
    print(fruit)  # যেহেতু Global Scope, তাই Function এর মধ্যেও Allow

    color = 'Green' # এটা Local Scope Only Function এর মধ্যে Available !
    print(color)


smallContainer('Orange') # Parameter আর Global Scope Same না!

# print(color) # Shows Not Defined !

def largeContainer():
    smallContainer('Mango')


largeContainer() # smallContainer Global Scope এ আছে!


# তাহলে Function Nested হতে পারে!

def movieType():

    type = 'Horror' # এটা এই Function এর সব জায়গায় Available !

    def movieName(name):
        print(type)
        print(name)

    movieName('Conjuring') # Maintain Indentation !!

movieType()

# যত পারবো Global Scope কম Use করবো!
```

```python
# Modifiying Global Scope In Local Scope

count = 1

def primary():
    # count = 2 # বাহিরের Count আর এই Count Same না
    # এটা আরেকটা Variable কিন্তু Same Name!
    # count += 1 # এইভাবে বাহিরের Count Modify করা যাবে না

    # global count += 1 # Modify করার জন্য এক Line এ লিখলে হবে না

    global count # Global কে Modify করার জন্য global Use করবো!!
    count += 1
    color = 'Red'
    print(count)
    print(color)

    # Nested Function এর Parent Scope Modify করা

    def secondary():
        nonlocal color # Parent কে Modify করার জন্য nonlocal Use করবো!!
        color = 'Orange'
        print(count)
        print(color)

    secondary()

primary()
```

### 📘 Step 2 — Data Structures & Algorithms

#### `List`

```python
# Data Structures

# Data Structure Use করা হয় Data Store, Organize And Manipulate করার জন্য

# List হলো Built-In Data Type যা Set Of Values Store করে
# যা Ordered, Mutable, Allows Duplicate
# একধরনের Heterogenous Arrays (Mixed Data Type)
# চেনার Way ? [ ] থাকবে !!!
```

```python
myList = [12,13,14,15,15,15,'Shourav', True]

print(f'myList = {myList}')

# List Properties Check করার জন্য

print(f'Data Types = {type(myList)}')
print(f'List Length = {len(myList)}')
```

```python
# Index Wise Ordered Maintain করে, String এর মতো Same
         #   0  1  2  3  4  5     6        7      Pos Idx
# myList = [12,13,14,15,15,15,'Shourav', True]
         #  -8 -7 -6 -5 -4 -3    -2       -1      Neg Idx

print(f'myList[6] = {myList[6]}')

print(f'myList[-2] = {myList[-2]}')


print(f'myList[-1:-3] = {myList[-2::]}') # String এর মতো Slice করা যাবে!
```

```python
# Mutable তাই Value Change করা যাবে

myList[-2] = 'Mahtabul'
myList[-1] = 'Shourav'

print(f'myList = {myList}')
```

```python
# List Traversing
# Iterate দুইভাবে করা যায় !!
# 1. Index Values Use করে 2. enumerate() Use করে যা পরে দেখবো!

print('Method - 1')
# 1. Index Values Use করে

# Length বের করতে হবে কারন For Loop কাজ করে Specific Number এর উপর!

# Length বের করার জন্য len() Use করবো !

for i in range(len(myList)):
    print(f'Index [{i}] = {myList[i]}') # Method - 1 Use করবো Always
```

```python
# List Methods
# কোনো Class এর Methods দেখার জন্য !

print(dir(list)) # Just Method Name দেখাবে !!

help(list) # Method এর Details দেখাবে !!
```

```python
# Useful Methods

myList = ['Apple', 'Banana', 'Orange']

# কোনো Element Last এ Add করার জন্য

myList.append('Cherry')

print(f'myList.append(\'Cherry\') = {myList}')

# Multiple Element Add করার জন্য

myNum = []

N = int(input('Enter Number Of Elements: '))

for i in range(N):
    x = int(input(f'Enter Element [{i}]: '))
    myNum.append(x)

print("myNum:", myNum)
```

```python
# কোনো Item Index Wise Remove করা And Store করার জন্য

myList = [1,2,3,4]

poppedItem = myList.pop(2)

print(f'Popped Item: {poppedItem}  After Pop myList: {myList}')
```

```python
# কোনো কিছুর Total বের করতে হলে

prices = [100, 250, 75, 50]

total = sum(prices)

print(f'Total Price: {total}')
```

```python
# Largest/Smallest Number বের করার জন্য

scores = [85, 92, 78, 99]

highest = max(scores)
smallest = min(scores)

print(f'Highest Score: {highest} \nSmallest Score: {smallest}')
```

```python
# Sorting করার জন্য

myNum = [11, 9, 3]

sortedList = sorted(myNum) # Acending Order

print(f'Sorted Num: {sortedList}')


sortedList = sorted(myNum, reverse=True) # Decening Order

print(f'Sorted Num: {sortedList}')
```

```python
# List কে Index And Value enumerate() Use করে

myFruits = ["Apple", "Banana", "Cherry"]
for i, fruit in enumerate(myFruits, start = 1): # Start = 1 Theke Start Hobe
    print(f"{i} = {fruit}")
```

```python
# List এর কিছু Usecase যা খুব Important
# 1. ১০০ টা '0' নিয়ে একটা লিস্ট Create করো
# 2. লিস্ট Concat করো
# 3. ১ থেকে ২০ এর একটা লিস্ট Create করো
# 4. List Unpacking & Packing
# 5. 2D List Create করো,Value Input করো
# 7. Copy লিস্ট
# 8. লিস্ট in, not in Operator
# 9. লিস্ট কে Reverse করো [::-1] 
```

```python
# 1. ১০০ টা '0' নিয়ে একটা লিস্ট Create করো

myList = [0] * 100

print(myList)
```

```python
# 2. লিস্ট Concat করো

myFruit = ['Mango', 'Watermelon', 'Orange']
myNumber = [1,2,3]

joinList = myFruit + myNumber

print(joinList)
```

```python
# 3. ১ থেকে ২০ এর একটা লিস্ট Create করো
myNum = list((range(1,21))) # Way 2

print(myNum)
```

```python
# 4. List Unpacking & Packing

myList = ['Mahtabul Shourav', 202331067042, 'CSE']

# List Unpacking যে কয়টা Item থাকবে সে কয়টা Variable = listName

Name, ID, Dept = myList

myDetails = f'Name: {Name} \nID: {ID} \nDept: {Dept}'

print(myDetails)

# এটার উল্টা তাই হলো List Packing
# listName = [যে কয়টা Item থাকবে সে কয়টা Variable]

myDetails = [Name, ID, Dept]
print(myDetails)
```

```python
# 5. 2D List Create করো, Value Input করো**

myList = [
#     C1    C2    C3                    Col = j
    ['A1', 'A2', 'A3'], # R1            Row = i
    ['B1', 'B2', 'B3'], # R2
    ['C1', 'C2', 'C3']  # R3
]
# So Basically Row Add করা হইতিসে !!!

print(len(myList)) # Number Of Row
print(len(myList[0])) # Number Of Col

for i in range(len(myList)):
    for j in range(len(myList[i])):
        print(myList[i][j], end=' ')
    print()


# 2D List User Input

row = int(input('Row: '))
col = int(input('Col: '))

myList = [] # Empty List

for i in range(row):
    rowList = [ ]
    for j in range(col):
        val = int(input(f'Enter Value [{i}][{j}]: '))
        rowList.append(val)
    myList.append(rowList)



# Visit All Elements
for i in range(len(myList)):
    for j in range(len(myList[i])):
        print(myList[i][j], end=' ')
    print()
```

```python
# 7. Copy লিস্ট

myList = [1, 2 ,3 ,4]

newList = myList.copy()

print(newList)
```

```python
# 8. লিস্ট in, not in Operator

myTeam = ['Shourav', 'Solaiman', 'Sihab']

# in
if 'Arnob' in myTeam:
    print('Yes')
else:
    print('No')


# not in
if 'Arnob' not in myTeam:
    print('Yes')
else:
    print('No')
```

```python
# 9. লিস্ট কে Reverse করো [::-1]

myList = [1,2,3,4,5]

reverseList = myList[::-1]

print(reverseList)
```


## **Step 9 — Advanced Language Power Features**
#### `Type Hinting & Annotations`

https://docs.python.org/3/library/typing.html
Type Hinting হচ্ছে একটা Way যা Python Code কে Document করতে, ঠিক Data Type দিতে Use করা হয় কিন্তু Python Code কিভাবে Run হচ্ছে তার উপর কোনো Effect পরে না ! 

Critical Benefits 
1. Readability
2. Error Checking

```python
# VariableName: Type = Value

fullName: str = 12 # No Error কিন্তু Wrong Type

print(f'{fullName} is a {type(fullName)}') # fullName আসলে একটা string হওয়া উচিত!
```

Install Static Code Analysis 

```bash
pip install mypy
```

Running Single Python File 

```bash
mypy filename.py
```

Now, It Will Display All The Type Hinting Errors 

```bash
main.py:3: error: Incompatible types in assignment 
(expression has type "int", variable has type "str")[assignment]
Found 1 error in 1 file (checked 1 source file)
```

Function Annotations 

```python
# def FunctionName(Par1: Type, Par2: Type, ..) -> Type:
#   return করলে Return Type/ print() করলে None

# Return Type
def addNum(numA: int, numB: int) -> int:
    return numA + numB

print(addNum(10, 20))


# None Type
def subNum(numA: int, numB: int) -> None:
    print(numA - numB)

subNum(10, 30)
```


