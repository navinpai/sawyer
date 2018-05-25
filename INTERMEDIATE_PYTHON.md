# Notes from [Intermediate Python](http://book.pythontips.com/en/latest/)

#### Iterators

```py
next(iterable) # Generates the next yield of the iterable
eg. next(gen_func)
```

```py
iter(iterable) # returns iterator to the iterator
eg. iter(str_var)
```

#### Ternary Operators

```py
(ifFalse, ifTrue)[test] # Alternate ternary operator
eg. fat = True; fitness = ("skinny","fat")[fat]
```

#### Classes

```py
class MyClass(object):
    # Tell Python not to use a dict, and only allocate 
    # space for a fixed set of attributes
    __slots__ = ["name", "identifier"]
    def __init__(name, identifier):
        self.name = name
        self.identifier = identifier
```

#### Enumeration

```py
# enumerate() maintains a running count
# second param is the (optional) start index, 1 in this case
for c, value in enumerate(my_list, 1):
    print(c, value)
```

#### Dict Comprehensions

```py
mcase = {"a": 10, "b": 34, "A": 7, "Z": 3}
mcase_frequency = {
    k.lower(): mcase.get(k.lower(), 0) + mcase.get(k.upper(), 0) 
    for k in mcase.keys()
}
# mcase_frequency == {"a": 17, "z": 3, "b": 34}
```

#### For/Else

```py
for item in container:
    if search_something(item):
        # Found it!
        process(item)
        break 
else: # Executes when for ends normally
    # Didn't find anything..
    not_found_in_container()
```

#### Coroutines

```py
def grep(pattern):
    print "Searching for %s" % pattern
    while True:
        line = (yield)
        if pattern in line: 
            print(line)

search = grep('coroutine') # We want to search for coroutine
search.next() # Start the coroutine
# Output: Searching for coroutine
search.send("I love you")
search.send("Don't you love me?")
search.send("I love coroutines instead!")
# Output: I love coroutines instead!
search.close() # Stops the coroutine
```

**Free Software, Hell Yeah!**