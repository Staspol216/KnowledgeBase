```js
const mock1 = "{()}";
const mock2 = "{[()[{}]]}";
const mock3 = "[[[[[[[]";
const mock4 = "[[{{(())}}]]";
const mock5 = "[{{}]]";

const openedBrackets = ["[", "{", "("];

const bracketsMap = {
  "}": "{",
  "]": "[",
  ")": "(",
};

const isValidBrackets = (brackets) => {
  const stack = [];

  const bracketsArr = brackets.split("");
  for (let i = 0; i < bracketsArr.length; i++) {
    if (openedBrackets.includes(bracketsArr[i])) {
      stack.push(bracketsArr[i]);
    } else {
      const lastOpenedBracket = stack.pop();
      if (lastOpenedBracket !== bracketsMap[bracketsArr[i]]) {
        return false;
      }
    }
  }

  return stack.length === 0;
};

console.log(isValidBrackets(mock1));
console.log(isValidBrackets(mock2));
console.log(isValidBrackets(mock3));
console.log(isValidBrackets(mock4));
console.log(isValidBrackets(mock5));
```
