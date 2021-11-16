# Testing and Modules

## Test Driven Development

Unit tests are pieces of code that serve to verify the input, output, and behaviour of our code.
Generally with Test Driven Development, it's good to think about tests first.
Lets say we wanted to test a function named `lowercase` that takes a string as an input and returns that
string but lowercase. Writing a test for it would look something like this:

```python

def test_should_return_lowercase_string():

  expected_string = lowercase('Alo')

  assert expected_string == 'alo'

```

### If name == main

Before executing code, Python interpreter reads source file and define few special
variables/global variables. If the python interpreter is running that module (the source file)
as the main program, it sets the special \_\_name\_\_ variable to have a value “__main__”. If this
file is being imported from another module, __name__ will be set to the module’s name. Module’s
name is available as value to __name__ global variable. 

This is important to know for cases where you might want to run a module standalone without
having to comment out code. The following code is a nice way to do this:

```python

def my_function():
    print ("I am inside function")

if __name__ == "__main__"
  my_function()

```
