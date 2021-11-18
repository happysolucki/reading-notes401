# Classes and Objects + Recursive Thinking

## Classes and Objects

Just like in javascript, classes in python serve as templates to create objects. The following 
is a demo of how we'd construct a class then create an instance of said class:

```python
class Cat:
  sound = 'meow'

  def function(self):
    print("This is a message inside the class.")
    
liam = Cat()
```

We can access variables and functions inside of objects using dot notation: `liam.sound`
We can change properties of objects the same way we can with javascript: `liam.sound = 'bark'`

## Thinking Recursively

When we want to solve problems recursively, we should first think about what condition should  
return a result. This is a _base case_. Say we want to write a function that returns the 
factorial of a number. In this instance, the base case would be this:

```python
def factorial_recursive(n):
  
  if n == 1:
    return 1
```

After accounting for base cases is when the recursive part comes in. It would look something 
like this:

```python
def factorial_recursive(n):
  
  if n == 1:
    return

  return n * factorial_recursive(n-1)
```
