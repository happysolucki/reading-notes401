# Dunder Methods

## Dunder Methods

Dunder methods allow us to emulate the behavior of built-in types. These 
methods are typically used to enrich classes. These methods got their name 
from being defined with preceding and trailing double underscores.
This design is know as the __Python data model__ and lets developers tap into 
rich language features like sequences, iteration, operator overloading, 
attribute access, etc.

Here are a couple examples of dunder methods:

### Object Initialization:\_\_init\_\_

The `__init__` dunder acts as a constructor method for classes:

```python
class Account:
    def __init__(self, owner, amount=0):
        
        self.owner = owner
        self.amount = amount
        self._transactions = []
```

### Object Representation:\_\_str\_\_,\_repr\_
It’s common practice in Python to provide a string representation of your 
object for the consumer of your class (a bit like API documentation.) There 
are two ways to do this using dunder methods:

1.__\_\_repr\_\_:__ The "official" string representation of an object. This is 
how you would make an object of the class. The goal of `__repr__` is to be 
unambiguous.

2.__\_\_str\_\_:__ The "informal" or nicely printalbe string representation of 
an object. This is for the enduser.

```python
class Account:

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
```
