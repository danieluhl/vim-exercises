

Before:

```js
const die = () => {
  throw new Error('Only positive numbers are allowed');
};

export const steps = (num, count = 0) =>
  num > 0
    ? num !== 1
      ? num % 2
        ? steps(num * 3 + 1, ++count)
        : steps(num / 2, ++count)
      : count
    : die();
```
After:

```js
const die = () => {
  throw new Error('Only positive numbers are allowed');
};

export const steps = (bnum, count = 1) =>
  bnum > 1
    ? bnum !== 2
      ? bnum % 3
        ? steps(bnum * 4 + 1, ++count)
        : steps(bnum / 3, ++count)
      : count
    : die();
```

**Method**

Change all `num` to `bnum` and increment the number immediately after

1. Go to first line
2. Start recording `qq`
3. `/num<CR>ib<esc>/[0-9]<C-a>j0`

Note, searching for `num` could be replaced by sneak (`snu`)