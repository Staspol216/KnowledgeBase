```js
const str = "one.two.three.four.five";

const createObj = (str) => {
  const obj = {};
  const keys = str.split(".");
  const stack = [{ obj }];

  for (let key of keys) {
    // @ts-ignore
    const { obj } = stack.pop();
    obj[key] = {};
    stack.push({ obj: obj[key] });
  }

  return obj;
};

console.log(JSON.parse(JSON.stringify(createObj(str))));

// RESULT
/*
{
  one: {
    two: {
      three: {
        four: {
          five: }
        }
      }
    }
  }
}
*/
```
