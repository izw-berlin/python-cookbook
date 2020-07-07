# Coding style
Some hints about general coding style

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
|Protected attributes (variables, fields, function, methods *|Use a leading underscore | _this_is_protected|

* The use of a leading underscore for protected identifiers is only a 
convention in Python and is of no meaning to the compiler/interpreter. 

## Function arguments


## Global variables
Do not use global variables to pass values from one function to another.
Global variables should only used for a true global state of a modul/program.

Global variables should only modified by global code, never as side-effect of
functions

In general, less global variables is better.

## Code formatting
Code formatting is an area that is highly dominated by personal preferences. Do not try
to push your preferences to others. I you work as a contributor on some project, follow
the formatting of the original author or lead maintainer.

But stay consistent in your code. 

Most IDEs have a function to auto format the code. Go to to the settings in the IDE for the
code formatting, adjust to your personal prefernces and then use the auto format feature.






