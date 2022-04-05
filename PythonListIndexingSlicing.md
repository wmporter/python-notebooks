## Python List Indexing and Slicing

[Slicing](#Slicing)

### Indexing

List indexing gets a particular list value based on its position. 

An index is specified using square brackets with the index between. 

Lists are zero-indexed, meaning that indexes are counted starting at 0. 

Indexes can also be negative, where -1 specifies the last item in the list. 

An index that is too large or too small will result in an error.


```python
#             Positive indexes
#          0    1    2    3    4    5
mylist = [403, 100, 656, 920, 150, 888]
#         -6   -5   -4   -3   -2   -1
#             Negative indexes
```


```python
# The first item is at index 0
print(mylist[0])
```

    403



```python
# The item at index 2 and index -4 are the same
print(mylist[2])
print(mylist[-4])
```

    656
    656



```python
# Index values can be stored in variables
index = -5
print(mylist[index])
```

    100



```python
# Sometimes you might have to calculate the index
a = 1
b = 3
print(mylist[a + b]) # a + b == 4
```

    150



```python
# Can't go outside the bounds of the list
mylist[7]
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-6-150404aef438> in <module>
          1 # Can't go outside the bounds of the list
    ----> 2 mylist[7]
    

    IndexError: list index out of range


### Slicing

Slicing a list creates a new list that contains part of the original.  
List slices are specified similar to indexes using square brackets.  
Each slice can have a start and stop value, separated by colons.

start - The list index where the slice will start. The slice will include the item at this index.  
stop  - The list index where the slice will stop. The slice will **_not_** include this index.

Why not include the stop index? One reason is that the length of the list can be used as the stop index.


```python
#                            Positive indexes
#             0    1    2    3    4    5    6    7    8    9
slicelist = [543, 905, 120, 345, 252, 112, 799, 104, 500]
#      -10   -9   -8   -7   -6   -5   -4   -3   -2   -1 
#                            Negative indexes
```


```python
# Get the first 3 items from the list
print(slicelist[0:3])
```


```python
# Get the last 4 items from the list
print(slicelist[5:9])
```


```python
# Get 3 items from the middle using negative indexes
print(slicelist[-6:-3])
```


```python
# Make a copy of the whole list
print(slicelist[0:len(slicelist)])
```

### Slightly Advanced Slicing

When creating a list slice, the start and stop indexes are optional. What happens if they are omitted?

start - If start is omitted, it will default to the start of the list  
stop - If stop is omitted, it will default to the end of the list

Another thing to keep in mind is that start and stop indexes are normalized. When using list slicing, Python will not complain about list indexes being out of range. 


```python
#                             Positive indexes
#             0    1    2    3    4    5    6    7    8    9
slicelist = [543, 905, 120, 345, 252, 112, 799, 104, 500]
#      -10   -9   -8   -7   -6   -5   -4   -3   -2   -1 
#                             Negative indexes
```


```python
# Get the first 3 items from the list by omitting the start
print(slicelist[:3])
```


```python
# Get the last 4 items from the list by omitting the stop
print(slicelist[5:])
```


```python
# Make a copy of the whole list by omitting both
print(slicelist[:])
```


```python
# The stop value is "normalized" to the length of the list if it's too big
print(slicelist[5:137])
```


```python
# The start value is "normalized" to the beginning of the list if it's too small
print(slicelist[-50:3])
```


```python
# A very weird way to get a copy of the whole list
print(slicelist[-999:999])
```

### Slightly More Advanced Slicing

In addition to start and stop, you can add a third number to list slices (separated with another colon) called step.

step - How many items to "count by" when slicing. Defaults to 1. Can be negative.

Adding a step value allows you to slice every other element from the list, for instance. All the same rules still apply. The slicing stops when the index of the next item is equal to (or more than) the stop value.


```python
#                             Positive indexes
#             0    1    2    3    4    5    6    7    8    9
slicelist = [543, 905, 120, 345, 252, 112, 799, 104, 500]
#      -10   -9   -8   -7   -6   -5   -4   -3   -2   -1 
#                             Negative indexes
```


```python
# Get every other item before item 5
print(slicelist[0:5:2])
```


```python
# Get every third item, starting at 1
print(slicelist[1::3])
```


```python
# What happens if we get every 50th item?
print(slicelist[::50])
```

### Extremely Advanced Slicing

In the Slightly More Advanced Slicing section, it's mentioned that step values can be negative. What does that mean?

A negative step value means that the list items are sliced from the right side of the list instead of the left. However, the new list that gets created is still built from left to right, which results in the new list having items in reverse order from the original.

Another thing this means is that the "end" indexes for start and stop are swapped. Instead of index 0 being the default for start, it's the last item of the list. Likewise, the default stop instead of 1 past the last item of the list is 1 before the first item.


```python
#                             Positive indexes
#             0    1    2    3    4    5    6    7    8    9
slicelist = [543, 905, 120, 345, 252, 112, 799, 104, 500]
#      -10   -9   -8   -7   -6   -5   -4   -3   -2   -1 
#                             Negative indexes
```


```python
# Get the last 3 values of the list in reverse order
print(slicelist[8:5:-1])
```


```python
# Every other item from the list from index 6 to 1, in reverse
print(slicelist[6:1:-2])
```


```python
# Without specifying a start, it starts at the end
print(slicelist[:4:-1])
```


```python
# Without a stop, it slices all the way to the beginning
print(slicelist[3::-1])
```


```python
# Get the entire list, but reversed
print(slicelist[::-1])
```
