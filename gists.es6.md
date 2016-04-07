## Curried summ function

```javascript
function curSum() {
  var args = Array.from(arguments).map(Number);
  var summ = args.reduce((a, b) => a + b, 0);
  
  function subSumm() {
    return curSum.apply(null, [summ].concat(Array.from(arguments)));
  }

  subSumm.valueOf = function() {
    return summ;
  }

  return subSumm;
}
```

## Simple curry

```javascript
function curried(fn, ...args) {
    return (...nArgs) => fn.apply(this, [...args, ...nArgs])
}
```

## Flatten

```javascript
const flatten = list => list.reduce(
    (a, b) => a.concat(Array.isArray(b) ? flatten(b) : b), []
);
```

## NodeList to Array

```javascript
var headings = [ ... document.querySelectorAll('h1') ];
```

## Unique Arrays

```javascript
[ ...new Set(array) ]
```

## Destructuring

```javascript
var {foo, bar} = {foo: "lorem", bar: "ipsum"};
// foo => lorem and bar => ipsum
```

## Max in array

```javascript
Math.max(...array);
```
## Only numbers in certain values

```javascript
  const ONLY_NUMBERS_REGEXP = /\D/g;

  if (ONLY_NUMBERS_REGEXP.test(value)) {
      fixedValue = value.replace(ONLY_NUMBERS_REGEXP, '');
  }
```