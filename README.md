# promise-race-map

A [`Promise.race`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race) implementation that works with JavaScript map.

## Background

[`Promise.race`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race) is useful when you need either one of the Promise to complete before proceeding. But if you need to process the result, it isn't easy to distinguish between two promises.

### Before using `promise-race-map`

Before using this package, you will need to write code like this.

```js
const p1 = fn1();
const p2 = fn2();

// Given both Promise do not return falsy values
const { r1, r2 } = await Promise.race([
  () => p1.then(res => ({ r1: res })),
  () => p2.then(res => ({ r2: res }))
]);

if (r1) {
  // Process result from fn1()
} else {
  // Process result from fn2()
}
```

### After using `promise-race-map`

After using this package, you can write shorter and more readable code like this.

```js
const { r1, r2 } = await Promise.race({
  r1: fn1(),
  r2: fn2()
});

if (r1) {
  // Process result from fn1()
} else {
  // Process result from fn2()
}
```

# Contributions

Like us? [Star](https://github.com/compulim/promise-race-map/stargazers) us.

Want to make it better? [File](https://github.com/compulim/promise-race-map/issues) us an issue.

Don't like something you see? [Submit](https://github.com/compulim/promise-race-map/pulls) a pull request.
