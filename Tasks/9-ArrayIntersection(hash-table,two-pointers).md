### Approach 1: Two Sets

---

```js
const input1 = [1, 2, 2, 1];
const input2 = [2, 2];
// Output: [2, 2];

const input3 = [4, 9, 5];
const input4 = [9, 4, 9, 8, 4];
// Output: [4, 9] or [9, 4]

const intersect = function (nums1, nums2) {
  let set1 = new Set(nums1);
  let set2 = new Set(nums2);
  return Array.from(new Set([...set1].filter((x) => set2.has(x))));
};

console.log(intersect(input1, input2));
console.log(intersect(input3, input4));
```

---

### Complexity Analysis

> Time complexity: O(n+m), where n and m are the arrays' lengths. O(n) time is used to convert nums1 into a set, O(m) time is used to convert nums2, and contains/in operations are O(1) in the average case.

> Space complexity: O(m+n) because in the worst case, when all elements in the arrays are unique, n space is used to store set1 and m space is used to store set2.

### Approach 2: Sorting and Two Pointers

```js
const input1 = [1, 2, 2, 1];
const input2 = [2, 2];
// Output: [2, 2];

const input3 = [4, 9, 5];
const input4 = [9, 4, 9, 8, 4];
// Output: [4, 9] or [9, 4]

const intersect1 = function (nums1, nums2) {
  const sortedNums1 = [...nums1].sort((a, b) => a - b);
  const sortedNums2 = [...nums2].sort((a, b) => a - b);

  let M = sortedNums1.length;
  let N = sortedNums2.length;
  let p1 = 0;
  let p2 = 0;

  console.log(sortedNums1);
  console.log(sortedNums2);

  const intersection = new Set();

  while (p1 < M && p2 < N) {
    if (sortedNums1[p1] == sortedNums2[p2]) {
      intersection.add(sortedNums1[p1]);
      p1++;
      p2++;
    } else if (sortedNums1[p1] < sortedNums2[p2]) {
      p1++;
    } else {
      p2++;
    }
  }

  return [...intersection];
};

console.log(intersect1(input1, input2));
console.log(intersect1(input3, input4));
```

---

### Complexity Analysis

> Time complexity: O(n logn + m logm), where n and m are the arrays' lengths. This dominating term comes from the need to sort both input arrays at the beginning of the solution.

> Space complexity: O(m + n) in the worst case when all elements in the arrays are different. This space is necessary to store and create the set intersection. The space used to store the result is not counted in the space complexity.
>
> Note that some extra space is used when we sort arrays in place. The space complexity of the sorting algorithm depends on the programming language.
>
> In Python/JavaScript, the sort method sorts a list using the Timsort algorithm which is a combination of Merge Sort and Insertion Sort and has O(n) additional space.
