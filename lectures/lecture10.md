# Week10 Python Boot Camp I: Basic Programming 

### Exam 2 is due

### [Lecture Stream](https://tamucc.webex.com/recordingservice/sites/tamucc/recording/playback/1c4324d948ef4a69a1aa5e0149981468)

___

## Computer Preparation

<details><summary>Windows - Ubuntu Setup (should already be done)</summary>
<p>

[Refer to the Instructions in the Resources Dir](../resources)

</p>
</details>


<details><summary>MacOS Terminal Setup (should already be done)</summary>
<p>
 
  * Open a terminal window
  
  * Consider installing [homebrew](https://brew.sh/).  You will be able to use homebrew to install linux software, such as `tree`, which is used in the slide show.
  
  * If the `CSB` directory does not exist in your home directory (check with `ls`), then run the following code to clone the `CSB` repository into your home directory:
  
    ```bash
    git clone https://github.com/CSB-book/CSB.git
    ```

</p>
</details>

___


## Install Anaconda

[Anaconda](https://www.anaconda.com/products/individual) is a free distribution of Python and R that includes preinstalled packages.  When you run `conda`, it is almost invisible but you will use its installations of Python and R rather than those that are already on your system.  While this may seem a bit confusing at first, the point of Anaconda is to make using Python easier.  It does this by allow you to maintain several "environments", with each environment being dedicated to a particular task with the dependencies that are unique to that task.  If you only maintain one environment in which you install all packages, they and their dependencies will start to conflict with each other. 

<details><summary>Don't take it from me, hear what ChatGPT has to say</summary>
<p>

Anaconda is a popular distribution of Python (and R) that offers several advantages, particularly for students who are new to programming or working in data science and machine learning. Here's why students might want to learn to use Anaconda:

1. Simplified Package Management: Anaconda simplifies the process of installing, managing, and updating Python packages. It comes with a package manager called conda, which makes it easy to install both Python packages and their dependencies with a single command. This is especially beneficial for beginners who might find the management of dependencies challenging.

2. Pre-installed Packages: Anaconda comes with a large number of pre-installed packages, particularly those used in data science, machine learning, and scientific computing. This saves time and effort in setting up the environment and allows students to start working on projects more quickly.

3. Environment Management: With Anaconda, students can create isolated environments for different projects. Each environment can have its own set of packages and Python versions, which is crucial when working on multiple projects with different dependencies. This feature helps in avoiding conflicts between package versions and ensures reproducibility of projects.

4. Ease of Use for Data Science Tools: Anaconda is particularly popular in the data science community. It includes packages like NumPy, Pandas, SciPy, Matplotlib, and Jupyter, which are staples in data analysis and visualization. Learning to use these tools within the Anaconda environment can be beneficial for students interested in data science.

5. Cross-Platform: Anaconda works across Windows, macOS, and Linux. This cross-platform support is beneficial for students as they can work in consistent environments regardless of their operating system.

6. Community and Commercial Support: Anaconda has a large community and commercial support, making it a reliable choice for educational and professional purposes. The community provides numerous resources, tutorials, and forums for learners.

7. Integrated Development Environment (IDE) Support: Anaconda Navigator, a graphical user interface included in Anaconda, makes it easier to launch applications and manage conda packages, environments, and channels without using command-line commands.

8. Focus on Analytics and Computation: Since Anaconda is tailored for data science and machine learning, it helps students focus more on analytics and computation rather than the intricacies of package management and environment setup.

In summary, for students, especially those in fields like data science, biology, engineering, and statistics, learning to use Anaconda can greatly facilitate their learning process by easing the setup and management of the tools they need for their studies and research.

</p>
</details>

---

<details><summary>Universal Anaconda Setup </summary>
<p>

Goto your terminal and download the most appropriate installer from the [anaconda downloads page](https://www.anaconda.com/download#downloads). Use the command line installer.  

```bash
cd Downloads

# ubuntu command line installer
wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh

# mac with intel cpu command line installer
wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-MacOSX-x86_64.sh

# mac with apple cpu (M1, M2, ..., etc) command line installer
https://repo.anaconda.com/archive/Anaconda3-2023.09-0-MacOSX-arm64.sh
```

Visit the [Anaconda Installation Page](https://docs.anaconda.com/free/anaconda/install/index.html)

Select the correct instructions for your computer.  For those with windows, use the Ubuntu terminal and follow the Linux instructions.

Install 

</p>
</details>

<details><summary>Old Win/Ubuntu Anaconda Setup </summary>
<p>
 

  * In Win10-Ubuntu terminal, `Anaconda` installation is a bit more challenging than just simply following `Anaconda` [download instructions](http://computingskillsforbiologists.com/setup/basic-programming/).  Here is how to make it work:

```bash
sudo apt update
sudo apt upgrade
cd ~
mkdir downloads
cd downloads
wget https://repo.anaconda.com/archive/Anaconda3-2020.07-Linux-x86_64.sh

# check data integrity
sha256sum Anaconda3-2020.07-Linux-x86_64.sh

# install
sudo bash Anaconda3-2020.07-Linux-x86_64.sh
```

Review the license agreement.  Note that the `d` key allows you to go down page by page.

If you see this message:

```bash
Anaconda3 will now be installed into this location:
/root/anaconda3

    - Press ENTER to confirm the location
    - Press CTRL-C to abort the installation
    - Or specify a different location below
```

We do not want to save to `/root/anaconda3`.  We want to save to `~/anaconda3`, but the installer does not recognize the ~. 

```bash
# if your installer is not pointed to ~/anaconda3, type the following
/home/YOURUSERNAME/anaconda3
```

When asked to initialize conda, do it. Finish the install, then when back in ubuntu, exit 

```bash
exit
```

Restart ubunutu terminal

```bash
cd ~

# make sure you have folder anaconda3
ls -d */

# set permissions
sudo chmod -R 777 anaconda3

# if it is still not on, you will see a (base) before your command prompt if it is on, then do this:
export PATH=~/anaconda3/bin:$PATH
conda init

# lastly, you can install jupiter notebook if you want, but we wont be using it
conda install jupyter
```


  * Using *Python*
  
    * open ubuntu terminal and type `python3`
	
  * Using Jupyter Notebook  (DONT USE JUPYTER NOTEBOOK FOR LECTURE)
  
    * In Win10-Ubunutu Terminal, first make sure the win10 `xming` app is running, then:
    
      ```bash
      #navigate to directory where you want to launch programming/
      jupyter notebook
      ```
      
    * If you installed anaconda in Win10, goto start menu and select `Jupyter Notebook (Anaconda3)`
	
    * In either, click `new` button in upper right corner, then `python3`
  
</p>
</details>

<details><summary>Old MacOS Anaconda Setup</summary>
<p>

[Anaconda](https://www.anaconda.com/products/individual) is a free distribution of Python and R that includes preinstalled packages.  When you run `conda`, it is almost invisible but you will use its installations of Python and R rather than those that are already on your system.  While this may seem a bit confusing at first, the point of Anaconda is to make using Python easier.

  *`Anaconda` should be installed following [instructions here](http://computingskillsforbiologists.com/setup/basic-programming/)
  
  * open terminal and type `python3`
  
  * To launch jupyter notebook (DONT USE JUPYTER NOTEBOOK FOR LECTURE)
  

</p>
</details>


<details><summary>Old Updating Anaconda Installation on MacOS/Ubuntu</summary>
<p>

Confirm that conda is running by checking for `(base)` before command prompt

```bash
(base) cbird@XPS15:~$
```

To update to latest version:

```bash
# this will take a while
conda update --all
```

To update to a specific version ([see list of versions](https://repo.anaconda.com/archive/)): 

```bash
# this will take a while
conda install anaconda=VERSIONNAME
```

You can also consult the [official documentation](https://docs.anaconda.com/anaconda/install/update-version/)

And also see [Keeping Anaconda Up To Date](https://www.anaconda.com/blog/keeping-anaconda-date)

</p>
</details>

___


## [I. Lecture Slides](https://github.com/tamucc-comp-bio/fall_2019/blob/master/lectures/Week05_files/Lecture05_BasicProgramming.pdf)

## II. Anaconda

### What is Anaconda?

[Anaconda](https://www.anaconda.com/products/individual) is a free distribution of Python and R that includes preinstalled packages.  When you run `conda`, it is almost invisible but you will use its installations of Python and R rather than those that are already on your system.  While this may seem a bit confusing at first, the point of Anaconda is to make using Python easier.


___

### Activating & Deactivating Anaconda

After you install Anaconda and restart, confirm that conda is running by checking for `(base)` before command prompt

```bash
(base) cbird@XPS15:~$
```

If conda is not on, you can turn it on:

```bash
conda activate
```

You can also turn `conda` off:

```bash
conda deactivate
```

___


### One More Time, What is Anaconda?

When `conda` is turned on, your default `python` will be that installed by `anaconda` and will include all the packages that `anaconda` preinstalls. You are not in a "conda command prompt", rather, `bash` is altered when `conda` is running.

You know that `conda` is running if your have `(base)` or something similar prior to your command prompt:

```bash
(base) cbird@XPS15:~$
```

Make sure `conda` is on for lectures and when completing assignments.

```bash
cbird@XPS15:~$ conda activate
(base) cbird@XPS15:~$
```

___


## III. Getting Started in Python (Ch 3.3)

### How to Run Python

We will work in `python3`. There are also legacy apps that require `python2` although `python2` is being phased out.

```bash
(base) cbird@XPS15:~$ python3
Python 3.7.3 (default, Mar 27 2019, 22:11:17)
[GCC 7.3.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

_*Note: you can exit `python3` enviroment with `ctrl+d`*_

___


### How to Get Help

* [ChatGPT](https://chat.openai.com)

* [docs.python.org](https://docs.python.org/3/)
  
* [stackoverflow.com](https://stackoverflow.com/)

```python
help()
help("My_COMMAND")  #pseudocode, replace My_COMMAND with the command you need help with
```

*_Note: `ctrl+d` exits the help environment if you are using python (without jupyter notebook)_*

___


### Simple Calculations and Basic Data Types

Math is much easier to code in `python` than `bash`.  The following code gives examples of some of the `python` data types:

* Integers    round numbers

* Floats    decimal numbers

* Booleans    TRUE, FALSE

* Strings    text
  
```python
# Math
>>> 2 + 2
4
>>> 2 - 1.5
>>> 2 * 2
>>> 3 / 2
>>> 3 // 2    #integer division
>>> 3 % 2    #modulo, or remainder of integer division

# Equalities
>>> 2 > 3
>>> 3 > 2
>>> 2 == 2
>>> 2 != 2    "not equal"
>>> 2 <= 2
>>> 2 >= 2

# Logical operations
>>> 1 < 2 & 2 < 3    "and"
>>> 1 < 2 | 2 > 3    "or"
>>> 1 < 2 ! 2 > 3    "not"

# Print text string
>>> "my string"
```

When text strings have single and double quotes, encapsulate the string in 3 additional pairs of quotes

```python
>>> """The tree's height is 6'2"."""
'The tree\'s height is 6\'2".'                  #' ignore this comment
```

Like `R`, `python` code obeys the standard order of mathematical operations, but using parentheses makes code more readable

*_P_*arentheses before

*_E_*xponents before

*_M_*ulitpy or 

*_D_*ivide before

*_A_*ddition or

*_S_*ubtraction

```python
>>> 2 * 3 ** 3
54
>>> 2 * (3 ** 3)
54
>>> (2 * 3) ** 3
216
```

___


### Variable Assignment

Variable assignment is similar to `R`

```python
>>> x = 5
>>> x
5
>>> who   #show user-defined variables, jupyter notebook only
x
>>> vars()   #works in python, not jupyter. others: globals(), locals(), dir()
{'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, 'x': 5}
```

*_Note: the output of `vars()` is in pairs.  Each item in a pair is delimited by `:`.  Each pair is delimited by `,`.*_

Math with variables

```python
>>> x + 3
8
>>> y = 8
>>> x + y
13
```

Variables can also store text, and like `R`, you must use quotes in `python3`. Further, mathematical operators can be used to paste text together, but variable data types must be the same

```python
>>> x = "The cell grew"
>>> x + " and is now larger"
```

You can not add a number and text together, unless the number is stored as a string or converted to a string

```python
>>> x + y
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'y' is not defined
>>> y=" 8 nm"
>>> x + y
'The cell grew 8 nm'
>>> y=8
>>> x + " " + str(y) + " nm"
'The cell grew 8 nm'
```

As you can see, `str()` changes the datatype to string.  Obviously, datatype is important in `python3`

```python
>>> z="88"
>>> type(z)
>>> y + int(z)    #change z datatype to integer
96
```

___


### Built-in Functions (a.k.a. Commands)

In `python3`, like `R`, each builtin function name is followed by parentheses that encapsulate the arguments passed to the function

```python
>>> s = "a long string"
>>> len(s)          #length, number of characters
13
>>> abs(-3.14)        #absolute value
3.14
>>> pow(3, 6)        #power, 3^6
729
>>> print(s)        #print variable to screen
a long string
>>> round(3.1415926535, 3)  #round to 3 decimals
3.142
>>> help(round)        #get help on round function
```

___


### Strings

Python has many useful functions for string manipulation.  We will start by making a string an counting the number of characters using `len()`

```python
>>> astring = "ATGCATG"
>>> len(astring)
7
```
  
Unlike `R`, `python3` is "*object-oriented*".  This means that each *object*, such as a *string variable*, has a set a functions specific to that *object*, called *methods*.  

```python
#Press tab twice after the period to list methods
>>> astring.
astring.capitalize(    astring.isdigit(       astring.rfind(
astring.casefold(      astring.isidentifier(  astring.rindex(
astring.center(        astring.islower(       astring.rjust(
astring.count(         astring.isnumeric(     astring.rpartition(
astring.encode(        astring.isprintable(   astring.rsplit(
astring.endswith(      astring.isspace(       astring.rstrip(
astring.expandtabs(    astring.istitle(       astring.split(
astring.find(          astring.isupper(       astring.splitlines(
astring.format(        astring.join(          astring.startswith(
astring.format_map(    astring.ljust(         astring.strip(
astring.index(         astring.lower(         astring.swapcase(
astring.isalnum(       astring.lstrip(        astring.title(
astring.isalpha(       astring.maketrans(     astring.translate(
astring.isascii(       astring.partition(     astring.upper(
astring.isdecimal(     astring.replace(       astring.zfill(
```
  
To learn more about a method, use `help`

```python
>>> help(astring.find)
```
  
*_Note: `q` will exit you from the help screen._*

Here are some examples of the string-specific methods

```python
>>> astring.replace("T", "U")
'AUGCAUG'

>>> astring.find("C")    #first position of C
3

>>> astring.count("G")
2

>>> newstring = " Mus musculus "

# split string with , 
>>> newstring.split()
['Mus', 'musculus']

# replace value with ,    similar to the bash command: tr "u" ","
>>> newstring.split("u")
[' M', 's m', 'sc', 'l', 's ']

# remove leading and trailig whitespace
>>> newstring.strip()        
'Mus musculus'
```

*_Note: two methods can be used in succession `astring.upper().find("C")`_*

String methods can also be applied to strings that are not stored in variables

```python
>>> "atgc".upper()
'ATGC'
>>> "TGCA".lower()
'tgca'
```
  
Concatenate strings with + (slow) or `join` (fast)

```python
>>> genus = "Rattus"
>>> species = "norvegicus"
>>> genus + " " + species
'Rattus norvegicus'

>>> human = ["Homo", "sapiens"]
>>> " ".join(human)
'Homo sapiens'

>>> "->".join(["one", "leads", "2", "the", "other"])
'one->leads->2->the->other'
```
  
Be careful not to confuse built-in *functions* with object-specific *methods*

```python
>>> s = "ATGC"

#call built in function print
>>> print(s)
ATGC

#there is no print method, so if you try to call it, it fails
>>> s.print()
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
AttributeError: 'str' object has no attribute 'print'
```

---

#### [Mind Expander 3.1](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUNllCM0VQNk1ZVDVXWUwzVlVVWVQzSEIxNy4u)

---

## IV. Python [Data Structures](https://docs.python.org/3/tutorial/datastructures.html) (ch 3.4)

Python provides built-in [data structures](https://docs.python.org/3/tutorial/datastructures.html) that are special types of objects that store data that is organized in a particular manner. It is important to learn to choose the right data structure for a particular task. 

* _Lists_ contain ordered sequences of values, termed *elements*

* _Dictionaries_ contain `key:value` pairs 

* _Tuples_ are lists where the elements cannot be changed or reordered

* _Sets_ are collections of distinct objects

___

### [Lists](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)


Defining lists

```python
# create an empty list 
>>> new_list = []

# create a list with elements, note that different data types can be used
>>> my_list = [3, 2.44, "green", True]

# the `list` function can be used to create a list
>>> a = list("0123456789")
>>> a
['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
```


Each element in a list is indexed, [starting at 0](http://python-history.blogspot.com/2013/10/why-python-uses-0-based-indexing.html), and elements can be retrieved by their index.

```python
# retrieve second value in `my_list`
>>> my_list[1]
2.44

# retrieve first value in `my_list`
>>> my_list[0]
3

# you will trigger an error if there is no element at the specified index
>>> my_list[4]
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

You can also set values of particular elements using the index

```python
# change first element of `my_list` to "blue"
>>> my_list[0] = "blue"
>>> my_list
['blue', 2.44, 'green', True]

# retrieve elements 0 to 1, not including 1
>>> my_list[0:1]
['blue']

# retrieve elements 1 to 3, not including 3
>>> my_list[1:3]
[2.44, 'green']

# retrieve all elements
>>> my_list[:]
['blue', 2.44, 'green', True]

# retrieve all elements before 3
>>> my_list[:3]
['blue', 2.44, 'green']

# retrieve all elements from three to the end of the list
>>> my_list[3:]
[True]

# retrieve the 2nd to last element
>>> my_list[-2]
'green'
```

The most useful methods for lists are:
```python
#`append` an element to the end of a list
>>> my_list.append(25)
>>> my_list
['blue', 2.44, 'green', True, 25]

#`copy` the list to a new list
>>> new_list = my_list.copy()
>>> new_list
['blue', 2.44, 'green', True, 25]

# `clear` all elements from a list
>>> my_list.clear()
>>> my_list
[]

#`count` occurences of a specified element in the list
>>> seq = list("TKAAVVNFT")
>>> seq.count("V")
2

#`index`, return the index of the first matching element
>>> seq.index("V")
4

#`pop` remove last element of a list an return it
>>> seq2 = seq.pop()
>>> seq
['T', 'K', 'A', 'A', 'V', 'V', 'N', 'F']
>>> seq2
'T'

#`sort` the elements in the list, best for numbers or characters
>>> a = [1, 5, 2, 42, 14, 132]
>>> a.sort()
>>> a
[1, 2, 5, 14, 42, 132]

#`reverse` the order of the elements in the list
>>> a.reverse()
>>> a
[132, 42, 14, 5, 2, 1]

#`del` an element or series of elements
>>> del(a[2:3])
>>> a
[132, 42, 5, 2, 1]
```

___


### [Dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

In an English dictionary, *definitions* are indexed by *words*.

In a  Python  dictionary, *elements*    are indexed by *keys*.

Syntax: `key:value, key2:value, key3:value ...`

```python
# Make an empty dictionary
>>> my_dict = {}

# like lists, dictionaries can contain several datatypes, not just 1
>>> my_dict = {"a": "test", "b": 3.14, "c": [1, 2, 3, 4]}
>>> my_dict
{'a': 'test', 'b': 3.14, 'c': [1, 2, 3, 4]}

# the order of the key:values do not matter in dictionaries
>>> GenomeSize = {"Homo sapiens": 3200.0, "Escherichia coli": 4.6, "Arabidopsis thaliana": 157.0}
>>> GenomeSize
{'Homo sapiens': 3200.0, 'Escherichia coli': 4.6, 'Arabidopsis thaliana': 157.0}

# call a specific key
>>> GenomeSize["Arabidopsis thaliana"]
157.0

# add a new value using a novel key
>>> GenomeSize["Saccharomyces cerevisiae"] = 12.1
>>> GenomeSize
{'Homo sapiens': 3200.0, 'Escherichia coli': 4.6, 'Arabidopsis thaliana': 157.0, 'Saccharomyces cerevisiae': 12.1}

# nothing happens if the key:value exists
>>> GenomeSize["Escherichia coli"] = 4.6
>>> GenomeSize
{'Homo sapiens': 3200.0, 'Escherichia coli': 4.6, 'Arabidopsis thaliana': 157.0, 'Saccharomyces cerevisiae': 12.1}

# the value is replaced if the key exists by the value is different
>>> GenomeSize["Homo sapiens"] = 3201.1
>>> GenomeSize
{'Homo sapiens': 3201.1, 'Escherichia coli': 4.6, 'Arabidopsis thaliana': 157.0, 'Saccharomyces cerevisiae': 12.1}
```

Useful dictionary methods

```python
# `copy` the dictionary
>>> GS = GenomeSize.copy()
>>> GS
{'Homo sapiens': 3201.1, 'Escherichia coli': 4.6, 'Arabidopsis thaliana': 157.0, 'Saccharomyces cerevisiae': 12.1}

# `clear` all elements 
>>> GenomeSize.clear()
>>> GenomeSize
{}

# `get` a value from a key, if the key doesn't exist then return a default value
>>> GS.get("Mus musculus", -10)
-10

# `keys`, create a list containing the keys in a dictionary
# useful to initialize a dictionary or return a special value when a key is not present
>>> GS.keys()
dict_keys(['Homo sapiens', 'Escherichia coli', 'Arabidopsis thaliana', 'Saccharomyces cerevisiae'])

# `values`, create a list containing the values in a dictionary
>>> GS.values()
dict_values([3201.1, 4.6, 157.0, 12.1])

#`pop`, remove the specified key from dictionary and return value
>>> GS.pop("Homo sapiens")
3201.1
>>> GS
{'Escherichia coli': 4.6, 'Arabidopsis thaliana': 157.0, 'Saccharomyces cerevisiae': 12.1}

# `update`, simplest way to join 2 dictionaries, order matters, keys in common will be overwritten. ' 
>>> D1 = {"a": 1, "b": 2, "c": 3}
>>> D2 = {"a": 2, "d": 4, "e": 5}
>>> D1.update(D2)
>>> D1
{'a': 2, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
```

___


### [Tuples](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences) 

Tuples are like lists, but can not be changed (write protection) and are faster.

```python
# define a tuple
>>> my_tuple = (1, "two", 3)

# return elements by indexing or slicing
>>> my_tuple[0]
1

# tuples cannot be changed
>>> my_tuple[0] = 33
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

There are only 2 methods for tuples

  ```python
  # `count` elements in tuple
  >>> tt = (1, 1, 1, 1, 2, 2, 4)
  >>> tt.count(1)
  4

  # `index`, return first index of element
  >>> tt.index(2)
  4
  ```

Tuples can also be used as keys in a dictionary

```python
>>> D3 = {("trial", 62): 4829}
>>> D3
{('trial', 62): 4829}
```

___


### [Sets](https://docs.python.org/3/tutorial/datastructures.html#sets)

Sets are lists without diplicated entries and have special operators.

* Union - values in set 1 *or* set 2

* Intersection - values in set 1 *and* set 2

* Difference - values unshared between set 1 and 2

```python
# create a list
>>> a = [5, 6, 7, 7, 7, 8, 9, 9]

# make a set from the list
>>> b = set(a)
>>> b
{5, 6, 7, 8, 9}

# intersection 
>>> c = {3, 4, 5, 6}
>>> b & c
{5, 6}

# union
>>> b | c
{3, 4, 5, 6, 7, 8, 9}

# difference
>>> b ^ c
{3, 4, 7, 8, 9}
```

The union, intersection, and difference operators also exist as *methods*. You can also test whether a set is a [subset](https://en.wikipedia.org/wiki/Subset) or a [superset](https://en.wikipedia.org/wiki/Subset). 

```python
# create sets using {}
>>> s1 = {1, 2, 3, 4}
>>> s2 = {4, 5, 6}

# intersection
>>> s1.intersection(s2)
{4}

# union
>>> s1.union(s2)
{1, 2, 3, 4, 5, 6}

# symmetric difference
>>> s1.symmetric_difference(s2)
{1, 2, 3, 5, 6}

# difference
>>> s1.difference(s2)
{1, 2, 3}

#subset
>>> s1.issubset(s2)
False

#superset
>>> s1.issuperset(s2)
False

>>> s1.issubset(s1.union(s2))
True
```

*_Note that calling `a = {}` creates and empty dictionary, not an empty set. `a = ([])` initializes an empty set._*

___


### Summary of Data Structures

```python
# round brackets -> tuple
>>> type((1, 2))
<class 'tuple'>

# square brackets -> list
>>> type([1, 2])
<class 'list'>

# curly brackets, seq of vals -> set
>>> type({1, 2})
<class 'set'>

# curly brackets, key:value pairs -> dictionary
>>> type({1: "a", 2: "b"})
<class 'dict'>
>>> one = (1, 2, "tuple")
>>> two = [3, 4, "list"]
>>> three = {5: ["value1"], 6: ["value2"]}   # a dictionary
```

The next level: Lists can also contain other lists, tuples, dictionaries.  If you think about it, a table is a list of lists.

```python
# create a list containing a tuple, list, and dictionary
>>> container = [one, two, three]
>>> container
[(1, 2, 'tuple'), [3, 4, 'list'], {5: ['value1'], 6: ['value2']}]

# add a value to the list within the dictionary within the list
>>> container[2][5].append("value3")
>>> container
[(1, 2, 'tuple'), [3, 4, 'list'], {5: ['value1', 'value3'], 6: ['value2']}]
```

___


### [Mind Expander 3.2](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMzdVVkQwTlRQMENSVTQ5S0dUT0c1NFgwRi4u)

---


