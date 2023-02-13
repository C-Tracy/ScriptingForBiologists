# Python Variable Types and Methods

## Variable Types
There are a wide array of variable types, many of which we will not need for this course. 
- Numeric: Integer, Complex Number, Float
- Dictionary
- Boolean
- Set
- Sequence Type: String, List, Tupule

The types we will use most (and are necessary in Exercise 2) are:
- Integers
- Dictionaries
- Strings
- Lists

Strings and lists are going to be one of our most common types when working with sequence data.

### String Methods

Let's first remember how to display the different methods available for strings
```
python3
DNA = "aatcgctactactga"
type(DNA) #Let's confirm our DNA variable is a string
dir(DNA) # Now let's see what methods are available on our variable
```
This is quite a long list, and we certainly will not need them all. 

Let's play around with a few in this list to see what they do.
Remember that our syntax for these methods are variablename.method():
```
# Let's first look at capitalize
DNA.capitalize()
# This just capitalized the first letter, but what about upper

DNA.upper()
# Here we capitalized every letter in our string

DNA.swapcase()
# Here we also capitalized every letter in our string
```

Now instead of changing the case of our DNA lets try to learn something useful about it.
```
#Let's first try to figure out the length of our sequence
DNA.count()
#This gave us the error that count() takes at least 1 argument, so isn't going to count all variables in our sequence.
#Let's be more specific about what we want to count.

DNA.count('G')
#We got 0, but if you look at the DNA sequence there are G's in it, however they are lowercase.

DNA.upper().count('G') #this will do the first method (making the dna upper) and then the second method of counting our G's
```
While we learned how to count specific nucleotides in our sequence we don't have our sequence length.
Instead of using count let's use the command len()
```
len(DNA) #this will return the length of our DNA string
```
One final string method that we will go over in this tutorial is replacement.

We can use .replace() to change one variable into another in our string.
Lets try this with complementary DNA sequences. 
```
DNA = "ATCGAAT"
print(DNA.replace("A", "T"))
```
Not bad! That was a pretty easy way to replace one variable with another. You could do this for all nucleotides to get your complementary DNA, but think about some other tools python offers that you could use. 

Let's move onto methods manipulating lists for now...

## List Methods
Now lets look at some methods available for strings that are related to our DNA sequences
```
DNA_list = ['ATCGCTAAATGTA', 'ATCGAATGTAAA']
dir(DNA_list)
```
Some of the methods that look useful are append, count, insert, index, reverse, and sort. Let's play with some of these
```
DNA_list.sort() #this will automatically sort our strings alphabetically

DNA_list.append('TAGC') #this takes one argument in the parentheses, and will append that argument onto the end of the list.
DNA_list #when we are in an interactive shell we can just call the variable name to print its value to the output
print(DNA_list) #lets go over using print statements though, that will print when running it as a script. 
```

## Print Statements
Print statements are used to print output for human's to read. Use these often as you are developing a script to make sure your script is doing what you think it is doing. 

```
#open an interactive python shell
python3 #if your python3 is installed as python or if you are using ipython you would change that accordingly here

# With print statements it is important to use quotes when you are printing an input string
print("Hello World")

# You can use either double or single quotation marks.
print('Hello World') 

```
Notice how the output is the same from the above two commands. 

Now if we wanted to print an existing variable we wouldn't use quotation marks.
```
greeting = "Hello World"
print(greeting)
```

### Return vs Print
As we saw above print will display the output in our terminal. It doesn't, however, feed this variable to our program. 
To provide the variable to your program you want to use the command 'return'.
This is necessary as we start working within functions in python. 

## Concatenation
Python makes is very easy to concatenate multiple strings together or strings along with variables.
Let's first try with undefined strings:
```
print("Hello " + "World")
```
Now lets try by defining our strings as variables:
```
sequence_a = "ATCG"
sequence_b = "AATT"
sequence_ab = sequence_a + sequence_b
sequence_ab #here we were able to concatenate the two sequences into a single sequence
```

## Dictionary
Instead setting up a code to replace sequences manually, we can create a dictionary to do the replacement
This may be useful if it is on a larger scale, and if it is a replacement you use often (such as the universal genetic code).

The general format is as follows:
dict = {key1:value1,key2:value2,key3:value3}

Let's see an example of one in use:
```
dict1 = {'bird':'frog', 'cat':'dog'}
dict1['bird']
#frog
dict1['frog']
#KeyError:'frog'
```
Remember that dictionaries are unidirectional and you cannot call the 'value' and get the matching 'key'
