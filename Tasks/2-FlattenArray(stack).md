```js
function flattenArray(stack) {
  const result = [];

  while (stack.length) {
    const el = stack.pop();

    if (Array.isArray(el)) {
      stack.push(...el);
    } else {
      result.unshift(el);
    }
  }

  return result;
}

const nestedArray = [1, [2, [3, 4], 5], 6];
console.log(flattenArray(nestedArray)); // [1, 2, 3, 4, 5, 6]
```
