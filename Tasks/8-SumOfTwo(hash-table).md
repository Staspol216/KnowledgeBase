```js
const getPair = (arr, sum) => {
  const nums = {};

  for (let i = 0; i < arr.length; i++) {
    nums[arr[i]] = i;
  }

  for (let j = 0; j < arr.length; j++) {
    const diff = sum - arr[j];
    if (diff in nums) {
      return [j, nums[diff]];
    }
  }

  return [];
};

console.log(getPair([2, 9, 0, 1, 3, 4], 14));
```
