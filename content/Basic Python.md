You already know the basics, so I am following a tutorial from W3schools and posting all the new things here.

# Python Basics
## Variables

Casting:
If you want to specify the data type of a variable, this can be done with casting.
Example:

```
x = str(3)    # x will be '3'  
y = int(3)    # y will be 3  
z = float(3)  # z will be 3.0
```

## Data Types
Python has the following data types built-in by default, in these categories:

| Text Type:      | `str`                              |
| --------------- | ---------------------------------- |
| Numeric Types:  | `int`, `float`, `complex`          |
| Sequence Types: | `list`, `tuple`, `range`           |
| Mapping Type:   | `dict`                             |
| Set Types:      | `set`, `frozenset`                 |
| Boolean Type:   | `bool`                             |
| Binary Types:   | `bytes`, `bytearray`, `memoryview` |
| None Type:      | `NoneType`                         |

## Type Conversion

Convert from int to float:
`a = float(x)`
## Random Number
Import the random module, and display a random number from 1 to 9:

```
import random  
print(random.randrange(1, 10))
```

## Strings are Arrays

Like many other popular programming languages, strings in Python are arrays of bytes representing unicode characters.
However, Python does not have a character data type, a single character is simply a string with a length of 1.
Square brackets can be used to access elements of the string.

```
a = "Hello, World!"  
print(a[1])
```
## Looping Through a String
Since strings are arrays, we can loop through the characters in a string, with a `for` loop.

```
for x in "banana":  
  print(x)
```

## String Length
To get the length of a string, use the `len()` function.

```
a = "Hello, World!"  
print(len(a))
```


# **Python Collections (Arrays)**
There are four collection data types in the Python programming language:

**List** is a collection which is *ordered and changeable.* *Allows duplicate members*.
**Tuple** is a collection which is *ordered and unchangeable. Allows duplicate members.*
**Set** is a collection which is *unordered, unchangeable*, *and unindexed. No duplicate members.*
**Dictionary** is a collection *which is ordered** and changeable. No duplicate members.*
## Lists

**Create a List:**

```
thislist = ["apple", "banana", "cherry"]
print(thislist)
```

Lists are:
1. Ordered
2. Changeable
3. Allow Duplicates

**List Length**:
To determine how many items a list has, use the len() function:
Print the number of items in the list:

```
thislist = ["apple", "banana", "cherry"]
print(len(thislist))
```

**Access Items:**
List items are indexed and you can access them by referring to the index number
Example:
Print the second item of the list:

```
thislist = ["apple", "banana", "cherry"]
print(thislist[1])
```

Here’s a list of commonly used functions and methods for **lists** in Python:
🔹 **Built-in List Methods**

These are functions **called on list objects** (e.g., `my_list.append(5)`):

| Method                          | Description                                                             |
| ------------------------------- | ----------------------------------------------------------------------- |
| `append(x)`                     | Adds element `x` to the end of the list                                 |
| `extend(iterable)`              | Adds all elements of an iterable to the end of the list                 |
| `insert(i, x)`                  | Inserts `x` at position `i`                                             |
| `remove(x)`                     | Removes the first occurrence of `x`                                     |
| `pop([i])`                      | Removes and returns the item at index `i` (last item if `i` is omitted) |
| `clear()`                       | Removes all items from the list                                         |
| `count(x)`                      | Returns the number of times `x` appears                                 |
| `sort(key=None, reverse=False)` | Sorts the list in place                                                 |
| `reverse()`                     | Reverses the list in place                                              |

🔹 **Useful Built-in Functions**
These are **global functions** that work with lists:

| Function         | Description                                            |
| ---------------- | ------------------------------------------------------ |
| `len(list)`      | Returns the number of elements                         |
| `sum(list)`      | Returns the sum of all elements (if numeric)           |
| `max(list)`      | Returns the maximum value                              |
| `min(list)`      | Returns the minimum value                              |
| `sorted(list)`   | Returns a new sorted list (original remains unchanged) |
| `reversed(list)` | Returns a reversed iterator                            |

**Loop Through a List**
You can loop through the list items by using a for loop:
Example
Print all items in the list, one by one:

```
thislist = ["apple", "banana", "cherry"]
for x in thislist:
  print(x)
```

```
thislist = ["apple", "banana", "cherry"]
for i in range(len(thislist)):
  print(thislist[i])
```

## Tuples

### **Create a Tuple:**

```
thistuple = ("apple", "banana", "cherry")
print(thistuple)
```

One item tuple, remember the comma:

```
thistuple = ("apple",)
print(type(thistuple))

#NOT a tuple
thistuple = ("apple")
print(type(thistuple))
```

### **Access Tuple Items**

```
thistuple = ("apple", "banana", "cherry")  
print(thistuple[1])
```

### **Change Tuple Values**
Once a tuple is created, you cannot change its values. Tuples are unchangeable, or immutable as it also is called.
But there is a workaround. You can convert the tuple into a list, change the list, and convert the list back into a tuple.

Example
Convert the tuple into a list to be able to change it:

```
x = ("apple", "banana", "cherry")
y = list(x)
y[1] = "kiwi"
x = tuple(y)

print(x)
```

### **Add Items**
1. Convert to a list
```
thistuple = ("apple", "banana", "cherry")
y = list(thistuple)
y.append("orange")
thistuple = tuple(y)
```

2. Add a tuple to a tuple: You are allowed to add tuples to tuples, so if you want to add one item, (or many), create a new tuple with the item(s), and add it to the existing tuple:
```
thistuple = ("apple", "banana", "cherry")
y = ("orange",)
thistuple += y

print(thistuple)
```

To **remove** items, convert to a list.

### **In built methods:**

| **Method / Function** | **Description**                       | **Example**             | **Output** |
| --------------------- | ------------------------------------- | ----------------------- | ---------- |
| `count(value)`        | Counts how many times a value appears | `(1, 2, 2, 3).count(2)` | `2`        |
| `index(value)`        | Returns the first index of the value  | `(5, 6, 7).index(6)`    | `1`        |
### **Other functions:**

| **Method / Function** | **Description**                          | **Example**          | **Output**         |
| --------------------- | ---------------------------------------- | -------------------- | ------------------ |
| `len(tuple)`          | Returns number of items in the tuple     | `len((1, 2, 3))`     | `3`                |
| `sum(tuple)`          | Returns the sum of elements (if numeric) | `sum((1, 2, 3))`     | `6`                |
| `min(tuple)`          | Returns the smallest item                | `min((4, 1, 8))`     | `1`                |
| `max(tuple)`          | Returns the largest item                 | `max((4, 1, 8))`     | `8`                |
| `value in tuple`      | Checks if value exists in the tuple      | `3 in (1, 2, 3)`     | `True`             |
| `tuple.index(val)`    | Raises error if not found                | `(1, 2, 3).index(4)` | `ValueError`       |
| `tuple unpacking`     | Assigns elements to variables            | `a, b = (10, 20)`    | `a = 10`, `b = 20` |
## Sets

### **Create a Set**
```
thisset = {"apple", "banana", "cherry"}
print(thisset)
```
Remember: **Sets are unordered**, so items may appear in a different order each time you print them.  
Duplicate values are ignored.
```
thisset = {"apple", "banana", "cherry", "apple"} 
print(thisset)  # {"apple", "banana", "cherry"}  (no duplicates)
```

### **Access Set Items**
Sets do **not support indexing** because they are unordered.  
But you can **loop through** or check membership.
```
thisset = {"apple", "banana", "cherry"}
for x in thisset:
    print(x)

print("banana" in thisset)   # True
```

### **Add Items**
```
thisset = {"apple", "banana", "cherry"}
thisset.add("orange")
print(thisset)
```

### **Remove Items**
```
thisset = {"apple", "banana", "cherry"}
thisset.remove("banana")   # Removes "banana"
print(thisset)

# remove() raises error if item not found
# discard() does NOT raise error
thisset.discard("pear")    # No error
```

### **Set Operators**
```
set1 = {"a", "b", "c"}
set2 = {"c", "d", "e"}

print(set1.union(set2))         # {'a', 'b', 'c', 'd', 'e'}
print(set1.intersection(set2))  # {'c'}
print(set1.difference(set2))    # {'a', 'b'}
print(set1.symmetric_difference(set2))  # {'a', 'b', 'd', 'e'}
```

In-place methods:
- `set1.update(set2)` → adds items from set2
- `set1.intersection_update(set2)` → keeps only common items
- `set1.difference_update(set2)` → removes items also in set2
- `set1.symmetric_difference_update(set2)` → keeps only non-common

### **In-built Methods**

| **Method**                    | **Description**                         | **Example**                             | **Output**      |
| ----------------------------- | --------------------------------------- | --------------------------------------- | --------------- |
| `add(x)`                      | Adds an element                         | `{"a","b"}.add("c")`                    | `{"a","b","c"}` |
| `update(iterable)`            | Adds multiple elements                  | `{"a"}.update(["b","c"])`               | `{"a","b","c"}` |
| `remove(x)`                   | Removes item, raises error if not found | `{1,2}.remove(2)`                       | `{1}`           |
| `discard(x)`                  | Removes item, no error if not found     | `{1,2}.discard(3)`                      | `{1,2}`         |
| `pop()`                       | Removes and returns a random element    | `{1,2,3}.pop()`                         | random element  |
| `clear()`                     | Removes all elements                    | `{1,2,3}.clear()`                       | `set()`         |
| `union(other)`                | Returns union                           | `{1,2}.union({2,3})`                    | `{1,2,3}`       |
| `intersection(other)`         | Returns intersection                    | `{1,2}.intersection({2,3})`             | `{2}`           |
| `difference(other)`           | Returns difference                      | `{1,2,3}.difference({2,3})`             | `{1}`           |
| `symmetric_difference(other)` | Returns non-common elements             | `{1,2,3}.symmetric_difference({2,3,4})` | `{1,4}`         |
| `issubset(other)`             | Checks if set is subset                 | `{1,2}.issubset({1,2,3})`               | `True`          |
| `issuperset(other)`           | Checks if set is superset               | `{1,2,3}.issuperset({2,3})`             | `True`          |
| `isdisjoint(other)`           | True if no common elements              | `{1,2}.isdisjoint({3,4})`               | `True`          |


### **Other Functions**

|**Function**|**Description**|**Example**|**Output**|
|---|---|---|---|
|`len(set)`|Number of elements|`len({1,2,3})`|`3`|
|`sum(set)`|Sum of numeric values|`sum({1,2,3})`|`6`|
|`min(set)`|Smallest value|`min({4,1,8})`|`1`|
|`max(set)`|Largest value|`max({4,1,8})`|`8`|
|`value in set`|Membership test|`3 in {1,2,3}`|`True`|

## Dictionaries
