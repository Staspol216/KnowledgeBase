## Fisher–Yates (aka Knuth) Shuffle

[Learn more about algorithm](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)

[Great visualization](https://bost.ocks.org/mike/shuffle/)

---

```js
const array = [1, 5, 3, 4, 7, 6, 0, 8];

const shuffleArray = (arr) => {
  for (let i = arr.length - 1; i > 0; i--) {
    const randomIndex = Math.floor(Math.random() * i);
    console.log(randomIndex);
    const temp = arr[i];
    arr[i] = arr[randomIndex];
    arr[randomIndex] = temp;
  }

  return arr;
};

console.log(shuffleArray(array));
```
