#### Sorting Numbers

JS's native `Array.prototype.sort` function sorts according to Unicode points, even when given an array of numbers. So `1` is put before `2`. Good. But `10` is also put before `2`. Not so good. You can get the right order by using the following:

```JS
arr.sort((a, b) => a - b);
```
