# Exceptions and error handling
In most cases exceptions are your friend: They prohibit working undetected with invalid values. And in many cases 
it makes the code more readable, because you don't always have to check the return value of functions.

If you have a backup strategy what to do if something fails, you can use the try statement to implement it (see references)

## Example
You map a symbolic name with a dictionary to a file path read some data from a file. 
If the symbolic name does not exist in your dictionary, it does not make sense to do any further work. 
At some time later ( at open()) you will get the next error. But the location of this shows not the 
true problem -> very bad for debugging

### Example A :

	DATA_MAP = { 'fox':'fox_data.csv', 'dog':'dog_data.csv' }
	
	data_file = DATA_MAP.get('cat')	# this will set data_file to None
	file = open(data_file)			# this will raise an exception about invalid parameter type

### Example B :

	DATA_MAP = { 'fox':'fox_data.csv', 'dog':'dog_data.csv' }

	data_file = DATA_MAP['cat']	# this will raise KeyError: 'cat'
	file = open(data_file)			# will not be executed

Both examples result in an exception, but in example A the exception will be on wrong line with 
misleading error message. The true problem is that you ask for 'cat' data, not anything with types... 

To heal the problem in example A you have to insert a check for the value of data_file after 
the assignment. And the only thing you can do at this place is to stop the program/function 
execution because opening a file with unknown name makes no sense. You have no advantage against example B.

If you have an alternate strategy how to handle unknown entries, it is a better way to 
implement by checking for the existence of the key in advance:

	DATA_MAP = { 'fox':'fox_data.csv', 'dog':'dog_data.csv' }

	data_name = 'cat'

	if data_name in DATA_MAP.keys():
		# key exists -> use dictionary for mapping
		data_file = DATA_MAP['cat']	
	else:
		# key does not exist -> use default name for data_file
		data_file = data_name+'_data.csv'
	file = open(data_file)			

## References :
- exceptions : https://docs.python.org/3/reference/executionmodel.html#exceptions
- try : https://docs.python.org/3/reference/compound_stmts.html#try
