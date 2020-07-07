# Classes, Properties and Accessors( getter/setter )
Access fields/attributes of a class only thru methods :getters and setters

## Why ?
1. encapsulate behavior associated with property
2. hide internal representation
3. make it possible to type-/range-check on setting
4. limit access to fields

## How ?
Convert all fields to protected and create properties for access where useful:
- make fields protected (in Python use leading underline)
- create getter for everything that is of interest from outside of class
- create setter for everything that is of useful to be set from outside of class
- it is possible (and sometimes useful) to create properties without corresponding field/attribute
- use the Python function property() or the @property decorator to defines properties

After defining the properties with property() or @property, the properties can accessed like 
'normal' fields/attributes. But every access is routed thru a method.

### getters :
- check that the state of the object allows access to property, otherwise raise exception
- because read access is with a method, it is possible to define calculated properties

### setters :
- only define setters for things that do not disturb the state of class
- check for valid type and/or range before changing field, if value is invalid raise exception
- if the internal state is dependent from the set value, update of invalidate internal state


## Example:
	class property_example:
	def __init__(self):
	self._x = 0
	self._y = 0

	""" Define read/write property with side effect (setting also self._y) and range check on set """
	@property
	def x(self):
	return self._x

	@x.setter
	def x(self,value):
	if not value >= 0: raise Exception('Value for x must be >=0')
	self._x = value
	self._y = value * value

	""" Define read-only property """
	@property
	def y(self):
	return self._y

	""" Define calculated read-only property """
	@property
	def z(self):
	return self._y * self._x

	pe = property_example()

	pe.x = 3 # OK
	pe.x = -3 # raise Exception: Value for x must be >=0
	print(pe.x)  # OK
	pe.y = 3 # raise AttributeError: can't set attribute
	print(pe.y)  # OK
	pe.z = 3 # raise AttributeError: can't set attribute
	print(pe.z)  # OK


References :
- property : https://docs.python.org/3/library/functions.html#property
- raise : https://docs.python.org/3/reference/simple_stmts.html#the-raise-statement
