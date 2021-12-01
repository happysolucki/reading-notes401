# Using Random Package, Risk Analysis, and Test Coverage

## Python Random Package

Python's Random module allows us to cause randomness, like generating random 
numbers or choosing random items from a list. Even though this module comes 
with Python, we have to import it to utilize it.

Say we wanted to generate a random integer that ranges from 1 to 10. We would do something like this: 

```python
import random

num = random.randint(1, 10)

```

As another example, we'd do this if we wanted to randomly choice an element 
from a list:

```python
import random

names = ["Brandon", "Tre", "Morgan", "Braxton"]

rand_name = random.choice(names)
```

## Risk Analysis

Risk Analysis is the process of identifying the risks in applications or 
software that you build and prioritizing them to test. Analyzing risks helps 
developers and managers mitigate them. Some of the possible risks one may need 
to think about are:

- Use of new hardware
- Use of new technology
- Use of new automation tool
- Sequence of code
- Availability of test resources for the application

## Test Coverage

Test coverage is a useful tool for finding untested parts of a codebase. It 
doesn't give any feedback on how good the test are though. It's pretty easy to 
have high coverage numbers with low quality testing. It's important to be 
thoughtful with the tests you write. Indicators of having quality testing is:

- You rarely get bugs that escape into production
- You are rarely hesitant to change some code for fear it will cause production bugs

### Resources

[How to use the Random Module in Python](https://www.pythonforbeginners.com/random/how-to-use-the-random-module-in-python)
[What is Risk Analysis](https://www.edureka.co/blog/risk-analysis-in-software-testing/)
[Test Coverage](https://martinfowler.com/bliki/TestCoverage.html)
