# List Comprehension

List comprehension is a powerful and concise method for creating lists in Python 
that becomes essential the more you work with lists, and lists of lists.

## Syntax

`my_new_list = [ _expression_ for _item_ in _list_ ]`

Three things are necessary for a python list comprehension to work:

1. First is the expression we’d like to carry out. _expression_ inside the square brackets.
2. Second is the object that the expression will work on. _item_ inside the square brackets.
3. Finally, we need an iterable list of objects to build our new list from. _list_ inside the square brackets.

Say we wanted to make a list of squares from 1 to 10. We could just do comprehension 
instead of a for loop:

```python
squares = [x**2 for x in range(1,11)]
```
