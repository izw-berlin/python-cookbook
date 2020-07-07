# Coding style
Some hints about general coding style. None of this hints is a fixed rule, but following
a consistent style makes life much more easy.

I you work in an organisation or company, follow the rules setup be the organisation/company. And
if you work as a contributor of a (big) project, follow the rules setup by the project author or 
lead maintainer.

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
|Protected attributes (variables, fields, function, methods \*|Use a leading underscore | _this_is_protected|

\* The use of a leading underscore for protected identifiers is only a 
convention in Python and is of no meaning to the compiler/interpreter. 

## Functions and Methods

### Names
The most common rule for the name of functions and methods is <verb>_<object> :
`print_data(data)`, `save_data(file_name, data)`, `print_report(data)`.


### Arguments


## Global variables
Do not use global variables to pass values from one function to another.
Global variables should only used for a true global state of a modul/program.

Global variables should only modified by global code, never as side-effect of
functions

In general, less global variables is better.

## Comments


## Code formatting
Code formatting is an area that is highly dominated by personal preferences. If there
is no bigger thing above you person, find your personal preferences. But stay consistent in your code. 

Do not try to push your preferences to others if you are not the project leader.

Most IDEs have a function to auto format the code. Go to to the settings in the IDE for the
code formatting, adjust to your personal prefernces and then use the auto format feature.

I you work as a contributor on some project, follow the formatting of the original author 
or lead maintainer. I you work in an organisation, follow the rules setup by the organisation.

Some useful formatting hints:
- Configure your editor/IDE to use Spaces as Tabs
- Most people use 4 (or 2) spaces for indention. Configure the tab-width in your editor/IDE to 4 (or 2).
- Structure the body of functions with empty lines between blocks of interrelated statments
- In function parameters put a space after the comma : `do_something(param1, param2, param3)` 

## Other guidelines and hints

### Explicit is better the implicit

### Do not try to be more clever than the compiler

### Code readability is more important than performance

### Do not make any assumptions about what the compiler does

### Avoid numeric constants / magic values in source




