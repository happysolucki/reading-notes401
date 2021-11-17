# Reading and Writing Files

## Opening and Closing a File

When wanting to work with a file, the first thing we should do is open it. When can 
do this by using the `open()` function. It takes a single argument which should be the 
file path. The function returns the file object.

`file = open('dog_breeds.txt')`

We should always close a file after opening it to prevent unwanted behavior.
One way to close a file is using a `try-finally` block:

```python
reader = open('dog_breeds.txt')
try:
    # Further file processing goes here
finally:
    reader.close()
```

A better way to do this is with a `with` block:

```python
with open('dog_breeds.txt') as reader:
  # Further file processing goes here
```

The `open()` function can take a second parameter that determines the mode in which the file 
is opened. By default, files are opened in read-only mode.

## Exceptions

Handling exceptions in python is similar to how it's done in JavaScript. 
In python, we can `raise` an exception to throw it:

```python
x = 10
if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))
```

In the code above we raised a custom exception.

Instead of `try` and `catch` blocks like in JavaScript, python has `try` and `except` 
blocks for handling errors/exceptions.

```python
try:
    linux_interaction()
except:
    pass
```

We can use `else` with these blocks to run code after we verify that there are 
no exceptions:

```python
try:
    linux_interaction()
except AssertionError as error:
    print(error)
else:
    print('Executing the else clause.')
```

We still have access to `finally` like we do in JavaScript:

```python
try:
    linux_interaction()
except AssertionError as error:
    print(error)
else:
    try:
        with open('file.log') as file:
            read_data = file.read()
    except FileNotFoundError as fnf_error:
        print(fnf_error)
finally:
    print('Cleaning up, irrespective of any exceptions.')
```

### Resources

[Reading and Writing Files in Python](https://realpython.com/read-write-files-python/)
[Python Exceptions](https://realpython.com/python-exceptions/)
