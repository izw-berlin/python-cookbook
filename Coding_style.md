# Coding style
Some hints about general coding style

## Identifiers (Names for things)
Identifiers should always be meaningful. Longer is in most cases better than short. But
how long they should be depends on the context. If the identifier is used only in a small
context, it could be shorter as if it used in a greater or global context. For example, it 
is not unusal to use single-letter-names for runnig variables in for-loops (iterators).

It is in general a good idea to follow the conventions of the used lanugage for
the definition style of identifiers:

### Names for constant values
Use upper case snake-style : THIS_IS_A_CONST_VALUE

### Names for classes
Use camel-case : MyClass

### Names for all other identifiers
Use lower case snake-style : this_is_a_normal_name

### Protected attributes (variables, fields, function, methods)
Use a leading underscore : _this_is_protected

## Function arguments


## Global variables
Do not use global variables to pass values from one function to another.
Global variables should only used for a true global state ofa modul/program.

In general less globals is better.






