### Итеративно

```js
const obj = {
  a: {
    b: {
      c: 1,
      d: 2,
    },
    e: 3,
  },
  f: 4,
};

const flattenObject = (obj) => {
  const stack = [{ obj, path: "" }];

  const dictionary = {};

  while (stack.length) {
    const { obj, path } = stack.pop();

    for (let key in obj) {
      const newPath = path ? [path, key].join(".") : key;

      if (typeof obj[key] === "object") {
        stack.push({ obj: obj[key], path: newPath });
      }

      if (typeof obj[key] === "number") {
        dictionary[newPath] = obj[key];
      }
    }
  }

  return dictionary;
};

// Ожидаемый результат: { 'a.b.c': 1, 'a.b.d': 2, 'a.e': 3, 'f': 4 } || { "f": 4, "a.e": 3, "a.b.c": 1, "a.b.d": 2 }

const flattenedObj = flattenObject(obj);
console.log(flattenedObj);
```

### Рекурсивно

```js
const flattenedObjR = (obj, path, result = {}) => {
  for (let key in obj) {
    const newPath = path ? [path, key].join(".") : key;

    if (typeof obj[key] === "object") {
      flattenedObjR(obj[key], newPath, result);
    }

    if (typeof obj[key] === "number") {
      result[newPath] = obj[key];
    }
  }

  return result;
};

// Ожидаемый результат: { 'a.b.c': 1, 'a.b.d': 2, 'a.e': 3, 'f': 4 } || { "f": 4, "a.e": 3, "a.b.c": 1, "a.b.d": 2 }

const flattenedObj2 = flattenedObjR(obj);
console.log(flattenedObj2);
```
