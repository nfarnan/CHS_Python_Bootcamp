# Input, Processing, Output (Gaddis Ch 2, 8)

## Hello World
* Create file with simply:

```python
print("Hello World!")
```

* Note simplicity, how that's handy for starting out with programming
	* Only introduce concepts as needed

* `print()` is a chunk of code written by someone else
	* Something you're going to be doing alot
	* Figure out the solution and reuse it

* Note you can print out multiple comma-separated items

* `"Hello World!"` is a string
	* Can also be `'single quoted'`
	* Or `"""TRIPLE QUOTED"""`

* Example of Python scripts and interpreter to highlight use of `"""`'s
	* `\n` and `\t` escape sequences
	* Escaping quotes within strings
	* `\\` to print a literal backslash


## Variable assignment
* Name on LHS, value on RHS
	* `=` is used, but not setting both sides to be equal
		* Assignment operator, not equality operator
		* Putting a constant on LHS will raise error

* Naming rules:
	* Can't use a keyword
	* No spaces
	* Must start will `a-zA-Z_`
	* After that, can contain `a-zA-Z0-9_`
	* Case sensitive

## Gathering user input
* `input()` examples

## String slicing
* Indexing individual characters
* Substring
* From some point to end
* From beginning to some point
* From beginning to end
* Negative indices
	* Can also be used as range bounds

## String operations
* `+` concat
* `*` repeat
* `len()` will tell you how many characters are in the string

## Numeric types
* `int`
	* Number with no fractional component
* `float`
	* Number with fractional component
* Note that variables can be reassigned new values
* Type is bound to the value, not to the variable
	* VERY different from many other languages (e.g., C, Java)
	* Will be odd for programmers in other languages
	* Will be intuitive for new programmers
	* This is *dynamic* typing
* Still *strongly* typed
	* Can't concat str and int

## Conversion
* `str()` can be used to convert int/float to str
	* Or any other object...
		* More on that later
* `int()` to parse an integer from a string
* `float()` to parse a float from a string

## Example time
```python
s = input("Enter a string to repeat:  ")
t = input("How many times should it be repeated?  ")
ti = int(t)

r = s * ti
print(r)
```

* First, remove `ti` and just reassign the value of `int(t)` to `t`
* Then, turn the `input()` and `int()` calls into a one-liner
* Then, turn the `print()` and repeat ops into a one-liner
* Highlight the need to maintain readability

## `None`
* Used to represent the absense of a value
* If you want to define a variable, but don't have a value for it yet, use `None`

## Numerical operations
* `+` add
* `-` subtract
* `*` multiply
* `/` divide
	* Demonstrate int/int yeilds a float
	* `//` floor division (aka integer division)
* `%` modulo (aka mod, aka remainder)
* `**` exponentiation
* Order of operations:
	* `()`
	* `**`
	* `*`, `/`, `//`, `%`
	* `+`, `-`
	* Tied operators eval'd left to right
	* Example:
		* `16 - 2 * 6 // 3 + 1`
		* == 13
		* Tie this back to computational thinking!
			* Break the complicated overall problem into subproblems
				* Any parens? Nope!
				* Any exp? Nope!
				* Any mul/div? Yes! Eval L -> R
				* Finally, eval add/sub L -> R
		* Note that if `//` is changed to `/`, the result becomes float
			* When one operand if float, result is float

## Augmented assignment
* Incrementing a variable:

```python
x = x + 1
```

* A bit too verbose, so we have:
	* `+=`
	* `-=`
	* `*=`
	* `/=`
	* `%=`
* Any C/Java programmers?
	* Note no `++` `--`

## format()
* Returns a string
* `format(a_float, [total][,][.after_dec]f)`
* `format(an_int,  [total][,]d)`
* If length of string is less than total, right aligned and padded with spaces

## Further print function details
* `sep=`
* `end=`

## "Magic" numbers
* Say you're writing a tax calculator for a 7% sales tax, why would this be a bad idea:

```python
total = subtotal * .07
```

* If the tax rate changes, you need to update the `.07` wherever its used!
* Do this instead:

```python
TAX_RATE = .07
total = subtotal * TAX_RATE
```

* Now, you'd just have to update the one instance of `TAX_RATE`
* In general, it is good practice to avoid unexplained literals
* THE ALL CAPS IS *CONVENTION* TO INDICATE A CONSTANT VALUE
	* Not actually guaranteed constant, just a variable
	* Python doesn't support formal constant values
		* Many other languages will for exactly this purpose


# Conditionals and Boolean logic (Gaddis Ch 3)

## The Boolean data type
* Only two possible values:
	* `True`
	* `False`
* Yes, caps are necessary

## Comparison operators
* Take in values, return a boolean
	* `==`
	* `!=`
	* `<`
	* `>`
	* `<=`
	* `>=`
* Simple for int/float, what about strings?
	* lexicographical order used for inequality ops

## Cool... but why? (if statements)
* Basic `if`
	* If boolean expression between `if` and `:` evals to true, execute body
	* Note that the "body" is a code block
		* Defined by indentation
		* Tabs vs spaces

```python
if num == 1:
	print("one!")
```

* `if` ... `else`

```python
if num == 1:
	print("one!")
else:
	print("not one...")
```

* Nested `if`'s
	* What happens if there is an `if` statement in the body of another `if` statement?
		* No problem!

```python
color = "blue"
if color[0] == "b":
	if color == "blue":
		print("blue!")
	else:
		print("something else with a \"b\"")
else:
	print("not blue!")
```

* `if` ... `elif` ... `else`

```python
if num == 1:
	print("one!")
elif num == 2:
	print("two!")
elif num == 3:
	print("three!")
else:
	print("not one or two or three...")
```

* Boolean operators
	* `and`
	* `or`
	* `not`
	* Precedence:
		* `not` first
		* `and` next
		* `or` last
		* All lower priority than comparison operators
		* All lower priority than math operators
	* Truth tables
	* Complex logic expression
		* Another example of computational thinking

```python
(True and False or False or not False) and not (False or False)
```


# Loops (Gaddis Ch 4)

## `while`
* Enter only if condition is `True`
* After completing loop body, recheck condition and, if still `True`, execute body again
* EX:

```python
count = 0
k = "y"
while k == "y":
	count += 1
	print("I've looped", count, "times!")

	k = input("Keep going? ")
```

* EX:

```python
i = 0
while i < 10:
	print(i)
	i += 1
```

## Infinite loops
* Beware!

```python
count = 0
k = "y"
while k == "y":
	count += 1
	print("I've looped", count, "times!")
```

## Sentinel values
* EX:

```python
num = int(input("Enter a number to square (-1 to stop):  "))
while num != -1:
	print(num, "squared is:", num ** 2)
	num = int(input("Enter a number to square (-1 to stop):  "))
```

* `-1` is our sentinel
	* Note this is different from the 10 in the previous example as we don't know how many iterations this loop will go through

## Input validation
* EX:

```python
num = int(input("Enter a number between 1 and 10:  "))
while num < 1 or num > 10:
	print("!! ERROR:", num, "is not between 1 and 10 !!")
	num = int(input("Try again:  "))

print(num, "is between 1 and 10!")
```

## Nested loops
* Sentinel + input validation

```python
num = int(input("Enter a number between 1 and 10 to square (-1 to stop):  "))
while num == 0 or num < -1 or num > 10:
	print("!! ERROR:", num, "is not between 1 and 10 !!")
	num = int(input("Try again:  "))

while num != -1:
	print(num, "squared is:", num ** 2)

	num = int(input("Enter a number between 1 and 10 to square (-1 to stop):  "))
	while num == 0 or num < -1 or num > 10:
		print("!! ERROR:", num, "is not between 1 and 10 !!")
		num = int(input("Try again:  "))
```

## `break`
* Immediately exit the current loop

```python
while True:
	num = int(input("Enter a number between 1 and 10 to square (-1 to stop):  "))
	while num == 0 or num < -1 or num > 10:
		print("!! ERROR:", num, "is not between 1 and 10 !!")
		num = int(input("Try again:  "))

	if num == -1:
		break

	print(num, "squared is:", num ** 2)
```

## `for`
* Only going in to example with `range()` for now
	* Because Gaddis wants to cover functions before collections...
		* Discuss your thoughts on this

* `# NEVER FORGET`
	* Easy to write malformed basic iteration, count bound `while` loops
	* `for` solves this problem

```python
for i in range(10):
	print(i)
```

```python
for i in range(2, 8):
	print(i)
```

```python
for i in range(1, 10, 2):
	print(i)
```

```python
for i in range(10, 2, -3):
	print(i)
```

* Note that while this is a common use of `for`, it is MUCH MORE POWERFUL than this

## `for` ... `else`
* Executed when you reach the end of what you're interating over

```python
for n in range(2, 10):
	for x in range(2, n):
		if n % x == 0:
			print(n, "equals", x, "*", n // x)
			break
	else:
		print(n, "is a prime number")
```

* Can also be applied to `while`
	* Executed whenever condition is `False`

## `continue`
* Skip to the next iteration of the current loop

```python
for num in range(2, 10):
	if num % 2 == 0:
		print("Found an even number", num)
		continue
	print("Found a number", num)
```

## Now you try it!
* Draw a left-tipped triangle

```python
for i in range(1, 6):
	for j in range(i):
		print("*", end="")
	print()
```

* Draw a right-tipped triangle

```python
LIMIT = 6

for i in range(1, LIMIT):
	for j in range(LIMIT - i - 1):
		print(" ", end="")
	for k in range(i):
		print("*", end="")
	print()
```

* Draw a middle-tipped triangle

```python
LIMIT = 10

for i in range(1, LIMIT, 2):
	sp = (LIMIT // 2) - ((i // 2) + (i % 2))
	for j in range(sp):
		print(" ", end="")
	for k in range(i):
		print("*", end="")
	print()
```

* Draw a diamond

```python
TBA
```


# Functions (Gaddis Ch 5, 12)

## y tho?
* Deduplication of code
* Ease of reuse
* Helps in breaking down complex problems
* Others... (that aren't of much use in an intro course...)
	* Testing
	* Faster dev
	* Ease teamwork

## Defining functions

```python
def message():
	print("Hello there!")
	print("How are you?")
```

## Calling functions
* Using name defined with `def` immediately followed by parenthesis

```python
message()
```

## Calling functions within functions

```python
def main():
	print("===START MESSAGE===")
	message()
	print("===END MESSAGE===")

def message():
	print("Hello there!")
	print("How are you?")

main()
```
* Trace through this example

## Scope and local variables
* **NEED ALL KINDS OF EXAMPLES HERE**
	* **CAN WING IT**
* Can define variables within a function, just like anywhere else
* Can't access variables defined in one function within another
	* Different *scope*
	* Can even have two different functions with variables with the same name
* Can't access variables defined in a function within the calling context
	* Or vice versa, with the exception of globals (no spoilers!)

## Global variables
* Defined outside of any function
* Available in all scopes in current file (or interpreter session)
* Bad practice to make use of global variables

```python
my_var = None

def record_score():
	my_var = int(input("Enter a score: "))

def repeat_score():
	print("Current score is:", my_var)

def print_message():
	my_var = "Hello" + " " + "There" + "!"
	print(my_var)
```

* Global scope variables used as constants are fine
	* E.g., `TAX_RATE` from awhile ago

## So how do we get values from one scope to another?
* Function arguments
	* Defined in the `()` of the `def` line
	* "Passed in" to the function when included in the `()` of the function call

```python
def say_hello(name):
	print("Hello,", name, "!")
```

* Local in scope to the function that are tied to
* If their value is changed in the body of the function, acts just like a local variable

* Keyword arguments
	* Specify a default value for the parameter
	* Can be omitted when calling the function
	* Can be mixed with positional parameters
	* Can have a value set during calling by either:
		* Placing a value at the appropriate position in actual parameter list 
		* Using `keyword=value` in actual parameter list
	* Note formal vs actual parameter semantics
	* **NEED TO WING IT WITH MORE EXAMPLES HERE**


## Return values
* If we want to encapsulate some computation within a function, we need a way to return the results
	* Just like `input()`!
	* Aptly, we can use `return`

```python
def repeat(name, times):
	return name * times

result = repeat("nick", 5)
```

```python
def get_num():
	x = int(input("Enter a number between 1 and 10 to square (-1 to stop):  "))
	while x == 0 or x < -1 or x > 10:
		print("!! ERROR:", x, "is not between 1 and 10 !!")
		x = int(input("Try again:  "))

	return x

num = get_num()
while num != -1:
	print(num, "squared is:", num ** 2)

	num = get_num()
```

* Note how we can change x to num in that example, it doesn't matter because of different scopes
* Write a `check_num()` function that returns a boolean

* Empty return vs no return
	* All None:

```python
def no_ret():
	print("No return")

def empty_ret():
	print("Empty return")
	return

def none_ret():
	print("None return")
	return None

print("None is")
print(type(None))

nr = no_ret()
print(type(nr))

er = empty_ret()
print(type(er))

noner = none_ret()
print(type(noner))

print(nr == er and er == noner and noner == nr)
```

## Using functions written by other people
* `import` allows you to bring in other peoples code
	* Python code resides in a *module*

* `random` module allows for easy generation of random numbers
	* Specifically using it's `randint()` function
		* Note that `randint()` is inclusive on the upper bound unlike `range()`
			* There is also `randrange()` which matches `range()`'s parameters

* The `math` module
	* What can it do?
		* Explore the Python standard library on the website!

## Recursion
* Functions that call themselves

* Infinite example:

```python
def message():
	print("Hello there!")
	message()

message()
```

* Try to trace through that, lol

### Base and recursive cases
* Base case, when you've the point that you should stop recursing
* Recursive case, when you realize you need to make another recursive call

* Write a recursive version of:

```python
for i in range(5):
	print(i)
```

* ANS:

```python
def rec_print(i):
	i -= 1
	if i < 0:
		# base case
		return
	else:
		# recursive case
		rec_print(i)
		print(i)
		return

rec_print(5)
```

* A simpler example:

```python
def message(times):
	if times > 0:
		# recursive case
		print("Hello there!")
		message(times - 1)

	# implicit base case

message(5)
```

* How about computing a factorial?

```python
def fact(n):
	if n == 0:
		# base case
		return 1
	else:
		# recurisve case
		return n * fact(n - 1)

print(fact(5))
```

* Trace this call stack

* What about a recursive alrgorithm to multiply two numbers?
	* Assuming the numbers are positive, nonzero ints

```python
def mult(x, y):
	if y > 0:
		# recursive case
		return x + mult(x, y - 1)

	else:
		# base case
		return 0

print(mult(3, 4))
```

* Discuss approaches to teaching recursion
	* E.g., Illustrate call stack on the board

# Files (Gaddis Ch 6)

## The files are *in* the computer
* Files will be stored on the hard drive
* In order to access their contents, you need to open them

## `open()`

```python
cur_file = open("filename.txt")
```

* This will allow you to read data out of filename.txt via `cur_file`

## Paths
* The first argument to `open()` is a string that represents a path to a file
* Hard drives are typically organized of heirarchies of files and folders
	* Files contain data
	* Folders contain files and other folders
	* (Ignoring partitions...)
* The folder at the top of the heirarchy is the *root* of the file system
	* Contains (directly or indirectly) all other files/folders on the drive
	* On Linux/macOS the root is simply `/`
	* On Windows the root is something like `C:\`
		* Windows has 1 root per drive
		* Linux/macOS have 1 root *period*
* A string listing the series of folders you would need to take to get from the root to the file in question is called a *path*
* When a path is given that does not start at the root, it is treated as a *relative path*
	* Picks up from the current directory
	* Hence, when we said to open "filename.txt", we were asking to open the "filename.txt" in the current working directory
		* Could be multiple different "filename.txt"'s on the same drive in different folders

## Reading from a file

```python
contents = cur_file.read()
```

* A bit inconvenient to read the entire file into a single variable...

```python
cur_line = cur_file.readline()
while cur_line != "":
	# process cur_line
	cur_line = cur_file.readline()
```

* Whenever there are no more lines in a file, it will return an empty string
	* How will we identify blank lines?
		* Will still have `"\n"` newline character!
			* Remember ASCII?

* Potential for easily creating infinite loops...

```python
for line in cur_file:
	print(line)
```

* Note that we couldn't actually run these one after another
	* After the call to `cur_file.read()`, there would be no more of the file to read!
	* One option is to use `seek()` to get back to the beginning of the file:

```python
cur_file = open("filename.txt")
contents = cur_file.read()

cur_file.seek(0)

for line in cur_file:
	print(line)
```

* Or we could re-open it
	* But then we'd need to close it first...

```python
cur_file = open("filename.txt")
contents = cur_file.read()

cur_file.close()
cur_file = open("filename.txt")

for line in cur_file:
	print(line)
```

* Good practice to always close a file you open
	* (Though Python is pretty forgiving and will generally close files for you)
	* Frees up resources dedicated to that file
		* Held by the Python interpreter and the OS
	* Great! Something else to forget!

## `with`

```python
with open("filename.txt") as cur_file:
	for line in cur_file:
		print(line)
```

* Will automatically close the file when you exit the `with` block!
* `with` is much more powerful than just this, but that's all we'll cover here

## What's with all the extra lines?!
* Remember the `"\n"` will be a part of the line read in
* And, `print()` by default adds a newline character
* Let's remove leading/trailing whitespace when we read in a line!
	* `str.strip()`
* Explore other string methods in Python

## File access modes
* So that allows us to read, what about to write?
* Have to open the file with a different *mode*
	* `"r"` read
		* Default if no mode is specified
	* `"w"` write
		* A new file will be created if one doesn't exist
		* If one does exist, its contents will be erased
	* `"a"` append
		* Writes will be appended to the end of the file
		* A new file will be created if one doesn't exist
	* `"r+"` read and write

* Now, we can make use of `write()`

```python
with open("filename.txt", "a") as cur_file:
	cur_file.write("A new line!\n")
```

## Binary files
* All of these examples assumed that we were working with *text* files
	* I.e., files formatted using the rules of some encoding like ASCII
		* Hence how Python knows how a line ends
* We could also read *binary* files
	* Don't assume any encoding rules, just treat it as a giant stream of bits
		* Broken up in to 8-bit chunks, bytes
* Can open a file in binary mode with a different mode spec:
	* `"rb"`
	* `"wb"`
	* `"ab"`
	* `"rb+"`
* Could open and process image files by opening them as binary files

# Exceptions (Gaddis Ch 6)

* Where can this go wrong:

```python
x = int(input("Enter a number:  "))
y = int(input("Enter a number:  "))

print(x, "divided by", y, "is", x / y)
```

* Check to make sure the user didn't enter a 0:

```python
x = int(input("Enter a number:  "))
y = int(input("Enter a number:  "))

if y == 0:
	print("Can't divide by 0!")
else:
	print(x, "divided by", y, "is", x / y)
```

## It's easier to ask for forgiveness than to ask for permission

```python
x = int(input("Enter a number:  "))
y = int(input("Enter a number:  "))

try:
	print(x, "divided by", y, "is", x / y)
except:
	print("Can't divide by 0!")
```

* Different handling for different errors:

```python
x = int(input("Enter a number:  "))
y = int(input("Enter a number:  "))

try:
	print(x, "divided by", y, "is", x / y)
except ZeroDivisionError:
	print("Can't divide by 0!")
except:
	print("What have you done now?!")
```

* Getting the details of the exception:

```python
x = int(input("Enter a number:  "))
y = int(input("Enter a number:  "))

try:
	print(x, "divided by", y, "is", x / y)
except ZeroDivisionError as err:
	print("Can't divide by 0!")
	print(err)
except Exception as err:
	print("What have you done now?!")
	print(err)
```

## `try` ... `except` ... `else`
	* If no `except`'s are tripped, run the `else` block

```python
try:
	with open("numbers.txt") as infile:
		total = 0
		for line in infile:
			total += int(line.strip())
except Exception as err:
	print(err)
else:
	print("The total is", total)
```

* Note that you can access `total` after the `try` statement (back in global scope)
	* However, it is dangerous to define it initially in the `try` block
		* Remove "numbers.txt" and note that the program crashes after hanlding the error trying to deal with total
		* Define it before entering the try block if you'll be using it outside
			* Else, exception could be encountered before its initialized!

## `try` ... `except` ... `else` ... `finally`
	* Whether we trip an `except` or the `else`, afterwards run `finally` block
	* Note that `else` isn't necessary, can have `try` ... `except` ... `finally`

```python
try:
	with open("numbers.txt") as infile:
		total = 0
		for line in infile:
			total += int(line.strip())
except Exception as err:
	print(err)
else:
	print("The total is", total)
finally:
	print("DONE")
```

* Note that we can also get in trouble if we reference `total` in the `finally` block
	* Same reason as referencing it after the entire `try`!


# Collections (Gaddis Ch 7, 9)

## Lists

* Mutable sequences of values

* **NEED EXAMPLES OF ALL OF THESE**
	* **CAN WING IT**

* Can be initialized with `[]`
* Can be indexed
* Can be sliced

* Size is dynamic, not pre-set like Java arrays or C arrays
	* More like Java ArrayList

* Can contain data of mixed types

* `len()` still applies here

* Has operators similar to strings:
	* `+` is a concatenation operator
	* `*` is a repetition operator
	* No vector math/matrix math support
		* For that, look to NumPy...

* Key list methods:
	* `list.append(x)`: add `x` to the end of the list
	* `list.remove(x)`: remove the first item from the list whose value is `x`
		```python
		a = [1, 2, 3]
		a.remove(2)
		a == [1, 3] #True
		```
	* `list.pop()`: remove the last item in the list
	* `list.pop(i)`: remove the item at index `i`
		```python
		a = [1, 2, 3]
		a.remove(1)
		a == [1, 3] #True
		```
	* `list.clear()`: remove all items from the list

### List comprehensions

* Note this is outside the scope of Gaddis...
* Consider creating a list of the squares of numbers 0 - 9:

```python
sq = []
for x in range(10):
	sq = x ** 2
```

* List comprehensions offer a shortcut syntax for things like this:

```python
sq = [x ** 2 for x in range(10)]
```

* Also supports an `if` clause:

```python
odd_sq = [x ** 2 for x in range(10) if x % 2 != 0]
```

* Can support multiple `for` clauses:

```python
t = [[x, y] for x in range(3) for y in range(3)]
```

* Also note that by making a list of lists, we've covered Pythons approach to 2D arrays

```python
t = [[x, y, z] for x in range(3) for y in range(3) for z in range(3) if x != y and x != z]
```

* Can be nested:

```python
t = [[str(x) + y for y in ['a', 'b', 'c']] for x in range(3)]
```

### Recursion revisited

* Write a recursive method to see if a given value is in a list (taking in a list and a value to search for):

```python
def find(l, v):
	if len(l) == 0:
		return False
	if l[0] == v:
		return True
	else:
		return find(l[1:], v)
```

* Now return the index that that value appears at and `-1` if it isn't in the list:

```python
def find(l, v):
	if len(l) == 0:
		return -1
	if l[0] == v:
		return 0
	else:
		rv = find(l[1:], v)
		if rv == -1:
			return rv
		else:
			return rv + 1
```

* How many recursive calls do we have to make?
	* `len(l)` in the worst case
	* Each recursive call reduces the number of indices left to check by 1
* Can we do it in fewer?
	* What about if we know the list is sorted?
		* Can cut the number of indices left to check in half
		* Check the middle
		* Recurse left or right accordingly

```python
def bin_search(l, v):
	return bs_rec(l, v, 0, len(l))

def bs_rec(l, v, low, hi):
	if v > l[hi - 1] or v < l[low]:
		return -1

	mid = (hi + low) // 2

	if v == l[mid]:
		return mid
	elif v < l[mid]:
		return bs_rec(l, v, low, mid)
	elif v > l[mid]:
		return bs_rec(l, v, mid + 1, hi)
	else:
		return -1
```

* How many recursive calls needed here?
	* Or: how many times can we divide the list in half before there is only 1 index left to check?
	* log<sub>2</sub>(n)
		* Where n is the length of the original list

* Would do Towers of Hanoi here
	* Book version uses only ints
	* Might be more intuitive to `append()` and `pop()` from lists to add/remove the "disks" from the "pegs"

## Tuples

* **IM**mutable sequences of values

* Can be initialized with `()`
	* or without...
* Can be indexed
* Can be sliced

* Cannot update an item in the tuple

```python
t = (1, 2, 3)
t[1] = 4  # ERROR
```

* Size cannot be changed (again, immutable!)

* Has operators similar to strings/lists:
	* `+` is a concatenation operator
	* `*` is a repetition operator
	* How are these allowed, I thought tuples were immutable?
		* They are, we're not modifying the tuple, but producing a *new* tuple
		* `3 + 5` does not change the value of `3` or `5`, for example

* How do you define an empty tuple?

```pyton
()
```

* What about a tuple with only 1 element?
	* `(1)` will be interpreted as using the paren operators in a math statement
	* The commas in tuples of more than 1 item disambuguate the syntax
	* But how do we define a singleton tuple?

```python
(1,)
```

* Trailing comma disambiguates meaning

* Actually, since the commas indicate a tuple, we can omit the parens:

```python
t = 1, 2, 3
type(t)  #<class 'tuple'>
```

* Note this means the following is not a syntax error!
	
```python
t = 1,
print(t)  #(1,)
```

* This is referred to as *tuple packing*

* Tuples can also be unpacked

```python
t = 1, 2, 3
a, b, c = t
print(a)
print(b)
print(c)
```

* Note that Python's ability to return multiple values is just tuple packing/unpacking

```python
def test()
	return 1, 2, 3  # packed into a tuple, return type is tuple

a, b, c = test()  # returned tuple is unpacked
```

## Dictionaries

* Key/value stores

* Initialization:

```python
d = {"key1":"value1", "key2":"value2"}
```

* Can be indexed
	* By keys

* **Cannot** be sliced
* Does **NOT** have `+` and `*` operators like strings/lists/tuples

* `{}` initializes an empty dictionary

### Dictionary comprehensions

* Work similarly to list comprehensions:

```python
dc = {x : x ** 2 for x in range(10)}
```

## Sets

* Unordered collections with no duplicate elements

* Cannot be indexed
* Cannot be sliced
* No `+` or `*`

* Initialized with `{}`

```python
s = {1, 2, 3, 3, 3, 4}
```

* Lack of key/value `:`'s disambiguates from dictionaries
	* But how do you define an empty set??
	
```python
s = set()
print(s)  # set()
s.add(1)
print(s)  # {1}
```

### Set operations

* `set.isdisjoint(other)`: True if the intersection of `set` and `other` is the empty set
* `set.issubset(other)`: True if `set` is a subset of `other`
	* Note that `<=` can also be used!
	* And `<` can be use for proper subset testing
* `set.issuperset(other)`
	* Note also have `<=` and `<`
* `set.union(*others)`
	* `|`
* `set.intersection(*others)`
	* `&`
* `set.difference(*others)`
	* `-`
* `set.symmetric_difference(other)`: Return a new set with the items in either but not in both

## Collection functions

* Like `set()`, we also have `list()`, `tuple()`, and `dict()`
	* Note that `dict()` is a little tricky:

```python
d = dict(one=1, two=2, three=3)
e = dict([("one", 1), ("two", 2), ("three", 3)])
f = {'one': 1, 'two': 2, 'three': 3}
d == e == f  # True
```

* Can be used to convert between different collection types:

```python
a = [1, 2, 3]
b = [3, 4, 5]
intersection = list(set(a) & set(b))
print(intersection)  # [3]
```

* Can also be used to covert other things to a collection:

```python
r = range(10)
type(r)  # <class 'range'>
l = list(r)
type(l)  # <class 'list'>
print(l)  # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

# OO (Gaddis Ch 10, 11)

## Primary programming paradigms:
* Procedural
	* What we have been doing so far, program is built up using different *procedures* or functions
* Functional
	* Makes extensive use of recursion
	* Built out of small, pure functions
* Object oriented
	* Currently the most popular
	* Centers around breaking your program up and splitting it amongst different objects

## Objects
* Contain both data (attributes) and code (methods)
	* Note the distinction of method vs. function
		* Former tied to object and operates on the object's data attributes
		* Latter object independent
* By moving data into objects, we can achieve *encapsulation*
	* Make it so that data attributes are accessible only via object methods
		* Accessors: methods only to get attribute values
		* Mutators: methods only to set attribute values
	* Note that we can't actually do strict encapsulation in Python...

## Classes
* The blueprint for an object
* Defining your own complex data type
* All of the code used by an object in defined within a class
* We create objects by *instantiating* classes
* Can have multiple instances (objects) of the same class

* Constructors
	* `__init__()`

* Other special methods:
	* `__str__()` returns a string representation of the object
		* `print(x)` is equivalent to `print(str(x))`
		* Essentially `toString()` from Java
	* `__repr__()` returns a representation of the object
		* repr() is implicitly called on items displayed by the Python interpreter

* All methods defined with `self` as the first parameter to the class
	* Is implicitly passed in calling, however

```python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age

	def display(self):
		print("Name:", self.name)
		print("Age:", self.age)
		print()

	def __str__(self):
		return self.name
	
	def __repr__(self):
		return "Person('" + self.name + "', " + str(self.age) + ")"

a = Person("Alice", 30)
print(a)
print(repr(a))
print(type(a))
a.display()
```

* "Private" attributes in Python:

```python
class Test:
	def __init__(self):
		self.a = "public"
		self._a = "private by convention"
		self.__a = "class-private"

t = Test()
print(t.a)
print(t._a)
print(t.__a)  # Error
print(t._Test__a)

t.a = "modified!"
t._a = "modified, too!"
t.__a = "this will error"  # Error
t._Test__a = "modified as well!"
print(t.a)
print(t._a)
print(t._Test__a)
```

* Class variables:
	* Defined outside of a method

```python
class Dog:
	tricks = []
	def __init__(self, name):
		self.name = name
	def add_trick(self, trick):
		self.tricks.append(trick)

f = Dog("Fido")
b = Dog("Buddy")
f.add_trick("roll over")
b.add_trick("play dead")
print(f.tricks)
```

* Note that attributes can be added outside of `__init__()` and futher outside of the class!
	* Empty classes can be used to just store data

```python
class Empty:
	pass

e = Empty()
e.test = 1
e.other_test = "another test!"

print(e)
print(repr(e))
print(type(e))
print(e.test)
print(e.other_test)
```

## Inheritance

* Chains of "is-a" relationships:
	* A student is a person
		* student: subclass
		* person: superclass
	* A dog is a mammal; a mammal is an animal
		* A mammal should have all the properties of an animal and then some
		* A dog should have all the properties of a mammal and then some

* Two approaches to developing chains of inheritance:
	* Specialization:
		* Top-down approach
		* Start with general classification
			* E.g., all people
		* Break into smaller groups based on group-specific attributes
			* E.g., students
	* Generalization:
		* Bottom-up approach
		* Start with individual groups
			* E.g., dog, cat
		* Identify shared attributes to define superclasses
			* E.g., mammals, animals

* Polymorphism
	* Allowing for different method definitions in super and sub classes

```python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age

	def display(self):
		print("Name:", self.name)
		print("Age:", self.age)
		print()

	def __str__(self):
		return self.name
	
	def __repr__(self):
		return "Person('" + self.name + "', " + str(self.age) + ")"

class Student(Person):
	def __init__(self, name, age):
		super().__init__(name, age)

		self.classes = []

	def add_class(self, new):
		self.classes.append(new)

	def display(self):
		super().display()
		print("Classes:", self.classes)
		print()

	def __repr__(self):
		return "Student('" + self.name + "', " + str(self.age) + ", " + str(self.classes) + ")"

def display_person(p):
	p.display()

a = Person("Alice", 30)
print(a)
print(repr(a))
print(type(a))

display_person(a)

b = Student("Bob", 20)
print(b)
print(repr(b))
print(type(b))

display_person(b)

b.add_class("CS1520")
print(b)

display_person(b)
```

* Multiple inheritance
	* Python allows it
	* Java does not
	* Allows for lattice of inheritance instead of strict heirarchy
		* A student-worker is a student and is a worker
			* Needs all properties of both

# Modules

* Any Python file is a module that can be imported into other Python modules with import

* Let `a.py` contain:

```python
def print_n():
	for i in range(10):
		print(i)

def print_l():
	for l in ["a", "b", "c"]:
		print(l)
```

* Can then (in other files):

```python
import a
a.print_n()
```

```python
from a import print_l
print_l()
```

* Consider:
	* Running python `a.py` from the command line
	* Having `import a` in another Python file
	* How can we have the former produce output while still being able to use the latter to pull in definitions??

	* Both will evaluate each line of a.py
		* However, `python a.py` will have `__name__` set to `"__main__"`
		* Hence, we can choose what to do if run as a script:
			* At the end of `a.py`, have:

```python
if __name__ == "__main__":
	print("Producing output!")
```

* Revisiting Person/Student example:

```python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age

	def display(self):
		print("Name:", self.name)
		print("Age:", self.age)
		print()

	def __str__(self):
		return self.name
	
	def __repr__(self):
		return "Person('" + self.name + "', " + str(self.age) + ")"

class Student(Person):
	def __init__(self, name, age):
		super().__init__(name, age)

		self.classes = []

	def add_class(self, new):
		self.classes.append(new)

	def display(self):
		super().display()
		print("Classes:", self.classes)
		print()

	def __repr__(self):
		return "Student('" + self.name + "', " + str(self.age) + ", " + str(self.classes) + ")"

def display_person(p):
	p.display()

def main():
	a = Person("Alice", 30)
	print(a)
	print(repr(a))
	print(type(a))

	display_person(a)

	b = Student("Bob", 20)
	print(b)
	print(repr(b))
	print(type(b))

	display_person(b)

	b.add_class("CS1520")
	print(b)

	display_person(b)

if __name__ == "__main__":
	main()
```

# Serialization

* Writing out a representation of objects to a file to reload their state later
* Can use pickle!

```python
import pickle

l = [1, 2, 3, 4, 5]
with open("test.pkl", "wb") as outf:
	pickle.dump(l, outf)

m = None
with open("test.pkl", "rb") as inf:
	m = pickle.load(inf)

print(m)
```

# Iterators and Generators

# Matplotlib

# Flowcharts

# Changes from 3rd Ed. to 4th Ed. of Gaddis:
* Python turtle graphics
	* Would be great for teaching elementary school programming
	* Would be great for students that want to build a graphic calcualtor
	* Other than that, meh
		* Still just programming for the sake of programming
* Matplotlib examples
	* Which we covered here
* GUI Programming subsection with the Canvas widget
* New appendices
	* E: using the `import` statement
	* F: using `pip` to install new packages
* New programming problems throughout

# Rest of the Pitt CS curriculum

* 0401: Intermediate programming in Java
	* Also offered through CHS!
	* More advanced OO
	* More advanced programming techniques overall
* 0441: Discrete structures
	* Logic
	* Counting
	* Probability
	* Relations
	* CS-based math background
* 0445: Data structures
	* How to implement a linked-list
		* How is it structurally different from an array?
	* Trees
	* Heaps
	* MUCH more advanced OO
	* Last of the core programming skills
* 0447: Intro to architecture
	* How does the CPU perform its "tricks"?
	* Overview of assembly
	* Basic system architecture
	* Should be able to (for a basic RISC architecture) "read" a binary instruction
* 0449: Intro to system programming
	* Learn C
	* Basics of interacting with an operating system
	* Threading
* 1501: Algorithm implementation
	* Tries/advanced searching techniques
	* Graph algorithms
	* Final test of programming skills
* 1502: Formal methods in CS
	* Proofs and further logic
	* Finite state machines
* 1550: Operating systems
* From here, electives!
