## Binary Search

Binary search works when you're searching for a value in a sorted collection. Just start in the middle of the collection, and see if the target value is higher or lower. Eliminate whichever half you can, and then go to the middle of the remaining half. Repeat until you find what you're looking for.

It can be implemented recursively:

```JS
function binarySearch(val, arr) {
  if (arr.length === 0) return -1;
  
  const midI = Math.floor(arr.length / 2);
  const midVal = arr[midI];
  if (val === midVal) {
    return midI;
  } else {
    if (val < midVal) return binarySearch(val, arr.slice(0, midI));
    if (val > midVal) return binarySearch(val, arr.slice(midI + 1));
  }
}
```

Or iteratively:

```JS
function binarySearch(val, arr) {
  let startI = 0, endI = arr.length - 1;
  
  while (startI <= endI) {
    const midI = start + (end - start) / 2;
    const midVal = arr[midI];
    if (val === midVal) {
      return midI;
    } else {
      if (val < midVal) end = midI - 1;
      if (val > midVal) start = midI + 1;
    }
  }
  
  return -1;
}
```

Also, you can use binary search on collections that obviously sorted, so long as you can efficiently determine which half to eliminate at each step. For example, suppose you're asked to fint the point of rotation in a rotated array. A rotated array isn't straightforwardly sorted, but given an random element, and given the values of the first and last element, you can determine whether you are before or after the point of rotation. Hence, a form of binary search is appropriate here.

#### Performance

Time complexity of binary search is `O(log n)`. Space complexity is `O(1)` for the recursive version and `O(log n)` for the recursive version.
