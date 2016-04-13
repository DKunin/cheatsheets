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


## Simple allpurpose mocker

```javascript
const loremIpsum = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque venenatis dui vitae hendrerit faucibus. In rutrum tincidunt ante. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Quisque quis erat at ipsum vehicula posuere ut ac purus. Phasellus elit urna, facilisis ut tellus et, tempus hendrerit velit. Proin ut vestibulum ex, eget dignissim felis. Morbi fermentum sagittis dolor vitae dapibus. Cras pretium nulla sed sapien luctus, constius ornare est rutrum. Vivamus aliquet, mauris ut accumsan pellentesque, metus nulla pulvinar nulla, ac commodo lorem lectus fringilla nisl.';

const statusesIds = [1, 2];
const problemIds = [1, 2, 3, 4, 5, 6];

const randomItem = function(arr) {
    return arr[Math.floor(Math.random() * arr.length)];
};

const randomEmail = function() {
    const strValues = 'abcdefg12345';
    let strEmail = '';
    let strTmp;
    for (let i = 0; i < 10; i++) {
        strTmp = strValues.charAt(Math.round(strValues.length * Math.random()));
        strEmail = strEmail + strTmp;
    }
    strTmp = '';
    strEmail = strEmail + '@';
    for (let j = 0; j < 8; j++) {
        strTmp = strValues.charAt(Math.round(strValues.length * Math.random()));
        strEmail = strEmail + strTmp;
    }
    strEmail = strEmail + '.com';
    return strEmail;
};

const lipsum = function(numberOfWords = 6) {
    const randArr = loremIpsum.split(' ');
    return Array.apply(null, { length: numberOfWords }).map(() => randomItem(randArr)).join(' ').toLowerCase();
};

export default function RandomGen() {
    return {
            statusId: randomItem(statusesIds),
            channelId: randomItem(statusesIds),
            problemId: randomItem(statusesIds),
            subject: lipsum(),
            typeId: randomItem(statusesIds),
            theme: randomItem(problemIds),
            problem: randomItem(problemIds),
            additional: randomItem(statusesIds),
            description: lipsum(),
            receivedAtEmail: randomEmail(),
            requesterEmail: randomEmail(),
            requesterName: lipsum(1),
            tags: ''
        };
}
```