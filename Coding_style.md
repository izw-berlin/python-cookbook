# Coding style
Some hints about general coding style. None of this hints is a fixed rule, but following
a consistent style makes life much more easy.

I you work in an organisation or company, follow the rules setup be the organisation/company. And
if you work as a contributor of a (big) project, follow the rules setup by the project author or 
lead maintainer.

All this rules and guidelines are not end to themselves. They exist to make life more easy.

## Comments are gold
Write comments about the steps in your program, the purpose and usage of functions and the purpose of
variables. Even the best programmers cant remember after month or years what he has done in the past. 
Comments make it much more easy to understand what is going on. For everyone, even the original creator.

For more guidelines about comments, see below.

## Identifiers (Names for things)
Identifiers should always be meaningful. Longer is in most cases better than short. But
how long they should be depends on the context. If the identifier is used only in a small
context, it could be shorter as if it used in a greater or global context. For example, it 
is not unusal to use single-letter-names for runnig variables in for-loops (iterators).

It is in general a good idea to follow the conventions of the used lanugage for
the definition style of identifiers:

|Type of identifier|Style                  |Example              |
|------------------|-----------------------|---------------------|
|Constant values   |upper case snake-style |THIS_IS_A_CONST_VALUE|
|Classes           |camel-case             |MyClass              |
|other identifiers |lower case snake-style |this_is_a_normal_name|
|Protected attributes (variables, fields, function, methods) \*|Use a leading underscore | _this_is_protected|

&#42; The use of a leading underscore for protected identifiers is only a 
convention in Python and is of no meaning to the compiler/interpreter. 

## Functions and Methods

### Names
The most common rule for the name of functions and methods is \<verb>_\<object> :
`print_data(data)`, `save_data(file_name, data)`, `print_report(data)`.

### Arguments
The name of function arguments follow the same rules as variable names.


## Global variables
Do not use global variables to pass values from one function to another.
Global variables should only used for a true global state of a modul/program.

Global variables should only modified by global code, never as side-effect of
functions

In general, less global variables is better.

## Comments

If possible, follow common conventions (like doxygen) about formatting of the comments, specially for
functions. If all comments for functions follow the doxygen convention it is possible to generate a 
documentation automatically.

The convention for doxygen comments are slight different for different programming languages. See the
documentation for doxygen: 
https://www.doxygen.nl/manual/docblocks.html#pythonblocks

## Code formatting
Code formatting is an area that is highly dominated by personal preferences. If you are not
part of a larger project, find your personal preferences, but stay consistent in your code. 
If you are contribute to a project started by other people, follow the formatting rules set by
the project leader for the project. I you work in an organisation, follow the rules setup by 
the organisation.

Do not try to push your preferences to others if you are not the project leader. 

Most IDEs have a function to auto format the code. Go to to the settings in the IDE for the
code formatting, adjust to your personal preferences and then use the auto format feature.

Some useful formatting hints:
- Configure your editor/IDE to use Spaces as Tabs
- Most people use 4 (or 2) spaces for indention. Configure the tab-width in your editor/IDE to 4 (or 2).
- Structure the body of functions with empty lines between blocks of interrelated statements
- In function parameters put a space after the comma : `do_something(param1, param2, param3)` 

## Other (general) guidelines and hints

### Avoid numeric constants / magic values in source
Most programs need constant values at different places. The simple (and bad) approach is to write
the constants direct as numerical value into the program. But this has two disadvantages:

- Often it is not easy to understand what this value means and how it is calculated. It looks _magic_.
- If something changes it is hard to find the values to change it. Specially if they are used in multiple
places.

For example, you have to convert something from per-minute to per-day. You can write:

    calculated_var = other_var * 1440
    
Everyone who reads this has to guess what the value _1440_ means. A better way is to define a variable
on top of the source code:

    MINUTES_PER_DAY = 1440
    
And write later:

    calculated_var = other_var * MINUTES_PER_DAY
    
With this every reader directly see that you convert something from a minute based value to a day based value.

---
Another example is the filesystem path to some (data) files.

Many programs must access files for reading or writing of data. To access this files they need to know 
where to find this files inside the filesystem. The simple, and bad method is to write the complete 
filename including the path direct as parameter to the file access function:

    import numpy as np
    ...
    # read content of datafile into an array of strings
    file_data = np.loadtext( "C:/mydata/project_MSc/ACCdata/fox.csv", dtype=str, delimiter='#')
    
If you move you data to another location of your computer or want to use data form another project you
have to search the source for all location where you access the data and change the file path.

A better solution is to define variables with all the needed information.

    # import needed libraries
    import numpy as np
    ...
    # set location and filename for ACC data
    DATAPATH    = "C:/mydata/project_MSc/ACCdata"
    DATAFILE    = DATAPATH+"/fox.csv"
    ...
    ...
    # read content of datafile into an array of strings
    file_data = np.loadtext( DATAFILE, dtype=str, delimiter='#')
    
Now, every change is easy. If you move all you data to another location, or want to access data from
another project, simply change the variable _DATAPATH_. If you want to run your program with data for
another species, simple change the variable _DATAFILE_.

Another god point of having this definitions at the top of the source file is, that it very easy to
see which external resource are needed to run your program. 


### Do not try to be more clever than the compiler / Code readability is more important than performance
Always write code for the human reader, not for the machine.

Modern languages and compiler are very good to find the best way to run a program. It is not (most times) 
needed to think about how to do a calculation in an efficient way. Let the compiler do it to find
the best way. 
 
Additionally to the point that it is only in rare cases possible to be better than the
compiler, modern computers are so fast that performance optimization will not have a great effect.  

As an example: You have a very complex arithmetic expression with different functions calls inside. Some
people think it is best to write it in one long expression, possible break down to multiple lines. 
But this way it can be difficult for a human reader to understand what is going on. A better way is to break 
it into multiple simpler sub-expressions with intermediate results and one finale expression with this
intermediate values. The compiler is very clever to understand that all the intermediate values are only
used for the final expression and will run it in the same way as the all-in-one expression, but now even a 
human reader can understand what is going on.


### Explicit is better then implicit
There are many possible cases for this. One example is the import and usage of functions from libraries:

The bad way:

    from numpy import *
    ...
    min_value = min(values)
With this version it is hard to find the source of the min-function. Is it from the python base or is it 
from an imported library.

The better way:

    import numpy as np
    ...
    min_value = np.min(values)
This way it is explicit written that the min-function comes from the numpy library  

---

Another example is the use of function parameters. In Python you have always the option to name the
parameters of a function call. If you write something like this:

    calculated_value = my_function( value1, value2, value3)    
Everyone has to lookup the definition of the function to find what value1, value2, and value3 mean. 

The better way is to write:

    calculated_value = my_function( day=value1, month=value2, year=value3)
This way everyone can see at the first view what the meaning of three values is. And additionally it is 
clearly to see that the function does something with a date, even if the function name does not show it.
     

### Do not make any assumptions about what the compiler does
Any compiler has a lot of things that are defined by the writer of the compiler. Normally this things should
follow a common convention. But the problem is, not for everything exist a common convention and not all
conventions are so common as one thinks...

Typical cases are:
- __Priority of operations__ in arithmetic expressions: There is a common convention, but it is not easy to 
remember it for all cases. +- vs. */ is easy, but what is about the other possible operations? Using 
parenthesis makes it explicit what order of evaluation is wanted/needed, independent of what the creator
of the compiler thinks or has done.
- __Execution order__ of functions in arithmetic expression or function parameters: Most inexperienced users 
will think it strict from left to right. __This is wrong!__ The execution order is, from the view of the 
user, complete random! If it is, for any reason, important that the functions are called in a definite 
order, you have to call the function sequentially before the use in an expression or as function parameters,
save the results to some variables and the do the expression of function call with the variables.
- __Type conversions__: If there are values of different data types in an expression, sometimes a value has to 
be converted from one data type to another. This can sometimes lead to strange results, specially if signed 
and unsigned values are mixed. Think twice about it. The compiler does not know what you think, you have to 
tell it. Basic rules are: 
    - signed is saver then unsigned
    - float is saver the integer

    But no in every case. Think twice about what you want to express and do it explicit if you are not sure
    that it is done in the right way.   

 
### Do not repeat yourself / Create functions for repeating tasks
If you use the same sequence of instructions on several places, create a function for it. If there are
__minor__ variations in instruction sequence create a function with a parameter to control the behavior.
But do not try to squeeze to different things into one function. If there are __major__ variations in 
the instruction sequence create another function. 

This has multiple reasons:
- If there is an error/mistake in your function sequence, you have to fix it only in on place.
- A very long function or program with dozens of lines is hard to understand. If the function
consist of only a few lines with calls to functions with self-explaining names it easy to understand it
on the first view.
- 





