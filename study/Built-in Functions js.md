
## ✅ Array Methods

### 1. forEach()
Executes a provided function once for each array element.
```js
[1, 2, 3].forEach((el) => console.log(el));
```

### 2. map()
Returns a new array with the results of calling a function on every element.
```js
const doubled = [1, 2, 3].map(n => n * 2); // [2, 4, 6]
```

### 3. filter()
Returns a new array with elements that pass the test.
```js
const evens = [1, 2, 3, 4].filter(n => n % 2 === 0); // [2, 4]
```

### 4. find()
Returns the first element that satisfies the condition.
```js
const firstLarge = [5, 10, 15].find(n => n > 8); // 10
```

### 5. some()
Returns `true` if **any** element passes the test.
```js
[1, 2, 3].some(n => n > 2); // true
```

### 6. every()
Returns `true` if **all** elements pass the test.
```js
[1, 2, 3].every(n => n > 0); // true
```

### 7. reduce()
Reduces the array to a single value.
```js
[1, 2, 3].reduce((acc, curr) => acc + curr, 0); // 6
```

### 8. includes()
Checks if array contains a specific element.
```js
[1, 2, 3].includes(2); // true
```

### 9. indexOf()
Returns the first index of a value, or -1 if not found.
```js
["a", "b", "c"].indexOf("b"); // 1
```

### 10. sort()
Sorts elements. Converts elements to strings by default!
```js
[3, 1, 2].sort(); // [1, 2, 3]
```

### 11. reverse()
Reverses the array **in place**.
```js
[1, 2, 3].reverse(); // [3, 2, 1]
```

### 12. flat()
Flattens nested arrays.
```js
[1, [2, [3]]].flat(2); // [1, 2, 3]
```

### 13. join()
Joins elements into a string.
```js
[1, 2, 3].join("-"); // "1-2-3"
```

---

## ✅ String Methods

### 1. includes()
```js
"hello world".includes("world"); // true
```

### 2. indexOf()
```js
"hello".indexOf("e"); // 1
```

### 3. slice()
```js
"hello".slice(1, 3); // "el"
```

### 4. toUpperCase() / toLowerCase()
```js
"Hi".toLowerCase(); // "hi"
```

### 5. trim()
```js
"  hello  ".trim(); // "hello"
```

### 6. split()
```js
"one,two".split(","); // ["one", "two"]
```

### 7. replace()
```js
"abcabc".replace("a", "x"); // "xbcabc"
```

---

## ✅ Object Methods

### 1. Object.keys()
```js
Object.keys({ a: 1, b: 2 }); // ["a", "b"]
```

### 2. Object.values()
```js
Object.values({ a: 1, b: 2 }); // [1, 2]
```

### 3. Object.entries()
```js
Object.entries({ a: 1 }); // [["a", 1]]
```

### 4. Object.assign()
```js
Object.assign({}, { a: 1 }, { b: 2 }); // { a: 1, b: 2 }
```

---

## ✅ Math Methods

### 1. Math.random()
```js
Math.random(); // e.g. 0.367
```

### 2. Math.floor(), Math.ceil(), Math.round()
```js
Math.floor(4.9); // 4
Math.ceil(4.1);  // 5
Math.round(4.5); // 5
```

### 3. Math.max(), Math.min()
```js
Math.max(1, 5, 3); // 5
```

### 4. Math.sqrt()
```js
Math.sqrt(9); // 3
```

---

## ✅ Date Methods

```js
const now = new Date();
now.getFullYear(); // 2025
now.getMonth();    // 0 to 11
now.getDate();     // day in the month
```

---

## ✅ JSON Methods

### 1. JSON.stringify()
```js
JSON.stringify({ a: 1 }); // '{"a":1}'
```

### 2. JSON.parse()
```js
JSON.parse('{"a":1}'); // { a: 1 }
```