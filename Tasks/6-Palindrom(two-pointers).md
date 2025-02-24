```js
/*
Примеры:
- Казак // true
- Madam, I'm Adam // true
- А в Енисее - синева // true
- О, духи, от уборки микробу-то и худо // true
- Не палиндром // false
*/

const isLetter = (letter) => {
  return letter.toLowerCase() !== letter.toUpperCase();
};

const isEqual = (letter1, letter2) => {
  return letter1.toLowerCase() === letter2.toLowerCase();
};

const isPalindorm = (str) => {
  let start = 0;
  let end = str.length - 1;

  while (start < end) {
    if (!isLetter(str[start])) {
      start++;
      continue;
    }

    if (!isLetter(str[end])) {
      end--;
      continue;
    }

    if (!isEqual(str[start], str[end])) {
      return false;
    }

    start++;
    end--;
  }

  return true;
};

console.log(isPalindorm("А в Енисее - синева"));
```
