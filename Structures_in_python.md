# C-like structures in Python
Sadly Python does not have a native type like structure in C (or record in Pascal) to put multiple 
associated values together. There are different possibilities to 'simulate' structures in Python and 
all have different pro's and con's:

## Using a List:
Pros:
- simple
- fast access with index
Cons:
- no symbolic names for the fields, only numeric indices (-> create const for name-to-index mapping)
- no type definition, every List is independent of all others of the same type
- no type annotation for fields

## Using a Dictionary:
Pros:
- simple
- symbolic names for the fields (the keys)
Cons:
- no type definition, every List is independent of all others of the same type
- access is a little bit slower than lists
- no type annotation for fields

## Using a 'degenerated' class (class without methods):
Pros:
- having a type definition 
- have symbolic field names
- usage is most similar to c structures
Cons:
- code can be confusing because they are not 'real' classes (-> put in comments)
- more complex to use, needs helper to create initialized instance 
Other:
- runtime penalty unclear 

## Using dataclasses.dataclass / @dataclass (Python >=3.7):
Pros:
- having a type definition 
- have symbolic field names
- usage is most similar to c structures
- decorator indicate that it is not a 'normal' class
- can have default values for fields

## Using collections.namedtuple (Python >=2.6):
Pros:
- having a type definition 
- have symbolic field names
- good for defining const structure-like types
- nice runtime behavior (small and fast)
Cons:
- resulting in immutable objects
- no type annotation for fields
- ugly syntax

## Using typing.NamedTuple (Python >=3.6): 
like @dataclass, but immutable type

## My preference for the different methods is: 
- use @dataclass for variable structures
- use NamedTuple for const structures


## References:
- c-like structures in python : https://stackoverflow.com/questions/35988/c-like-structures-in-python
- @dataclass : https://docs.python.org/3/library/dataclasses.html
- namedtuples : https://docs.python.org/3/library/collections.html#collections.namedtuple
- NamedTuples : https://docs.python.org/3/library/typing.html#typing.NamedTuple

