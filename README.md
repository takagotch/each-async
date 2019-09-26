### each-async
---
https://github.com/sindresorhus/each-async

```js
// test.js
import test from 'ava';
import m from './';

test.cb('async tasks will run parallelly', t => {
  const fixture = [];
  const actual = [];
  
  m(fixture, (el, i, next) => {
    setTimeout(() => {
      actual.push(el);
      next();
    }, Math.random() * 2000);
  }, () => {
    t.is(actual.length, fixture.length);
    t.notDeepEqual(actual, fixture);
    t.end();
  });
});

test.cb('stop iteration on first error', t => {
  let j = 0;
  
  m([1, 2, 3], (el, i, next) => {
    j++;
    next(true);
  }, () => {
    t.is(j, 1);
    t.end();
  });
});
```

```
```

```
```


