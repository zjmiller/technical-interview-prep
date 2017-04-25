## Core: Using Maps

A map associates one piece of data with another piece of data. (Hence, they are sometimes called associative arrays.) Often this will involve associating something (string, integer, or whatnot) with an integer. You can use this kind of map to count how many times something occurs within a larger structure: e.g., how many times a character occurs in a string or an integer occurs in an array of integers.

The following code snippet shows how to count how many times each character occurs in a string. Pretty much the exact same code works to count how many times each integer occurs in an array of integers.

```JS
  const myMap = new Map();
  
  for (let i = 0; i < str.length; i++) {
    const char = str[i];
    if (myMap.has(char)) myMap.set(char, myMap.get(char) + 1);
    else myMap.set(char, 1);
  }
```

If you're using JavaScript, you can use the built-in `Map` object. It's also easy to see how to use a plain JS object to serve as a map. The `Map` object's most important methods are `has`, `get`, `set`, and `delete`. You can see how the first three work by looking at the code snippet above, and `delete` is pretty self-explanatory.

Speaking loosely, whenever you need to count elements, you should consider using a map. It can be a little bit tricky to figure out when this is what you need to be doing. For example, suppose you're asked whether two strings are permutations of each other. You could reframe this as: do these two strings have the same number of A'a, the same number of B's, etc.? When thought of like this, the problem clearly concerns counting things, and hence is can be approached via a map.

```JS
  const myMap = new Map();
  
  for (let i = 0; i < str1.length; i++) {
    const char = str1[i]
    if (myMap.has(char)) myMap.set(char, myMap.get(char) + 1);
    else myMap.set(char, 1);
  }
  
  for (let i = 0; i < str2.length; i++) {
    const char = str2[i]
    if (!myMap.has(char)) return false;
    else myMap.set(char, myMap.get(char) - 1);
    if (myMap.get(char) === 0) myMap.delete(char);
  }
  
  return true;
```

#### Quick Side Note

When asked whether two strings/arrays are permutations of each other, a nice optimization is to first make sure they're the same length. If they aren't the same length, you know they're not permutations even before accessing any of the elements. Very similar optimizations occur in different contexts. For example, if asked whether a string contains any character more than once, one thing you can do is check whether the length of the string exceeds the number of different possible characters (you'll have to inquire into the underlying character set).

#### Performance

A map is abstract data type. It can be implemented in different ways. In JS the implementation is left more or less open by the spec, which just says the following:

> Map object must be implemented using either hash tables or other mechanisms that, on average, provide access times that are sublinear on the number of elements in the collection.

Maps are typically implemented using a hash table or a (self-balancing) binary search tree. Both of these structures provide sublinear access times. The details are complicated, but basically, a hash table provides `O(1)` access in the average case and `O(n)` access in the worst case, while a balanced BST provides `O(log n)` access in both the average and worst case.
