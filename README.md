## Language

US English should be used.

__preferred__
```js
var authorized = true;
```

__not preferred__
```js
var authorised = true;
```

## Semicolons

Use semicolons.

Do not place semicolons after any `function` unless it is a declaration (like `var y = function(){};`).

Don't omit the semicolon after `return`.

__preferred__
```js
var x = 12;
var y = function(){};

for (var i = 0, l = 5; i < l; i++) {
  // something
}

function handler() {
  // something
  return;
}
```

__not preferred__
```js
var x = 12
var y = function() {}

for (var i = 0, l = 5; i < l; i++) {
  // something
};

function handler() {
  // something
  return
};

;
```

## Naming

All names should be limited to using alpha `a-z` and numeric `0-9` characters. All names should start with an alpha character. One exception is when dealing with an outside dependency, like SQL, where a column name may contain underscores.

Names should be camel cased. Any constructor should start with a capital letter. Any other type of variable should start with a lowercase character.

Constants do not exist in Node, since the idea of a frozen variable is loose. Global variables should be named like normal variables.

__preferred__
```js
var defaultValue3 = 30;

function Parent() {
  this.myValue1 = 10;
  this.myValue2 = 20;
  this.myValue3 = defaultValue3;
}
var child = new Parent();
```

__not preferred__
```js
var DEFAULTVALUE3 = 30;

function parent() {
  this.MyValue1 = 10;
  this.myvalue2 = 20;
  this.my_value_3 = 30;
}
var Child = new Parent();
```

## Function Declarations

If possible, do not define a function, rather than assigned a function to a variable.

__preferred__
```js
function doSomething() {}
```

__not preferred__
```js
var doSomething = function() {}
```

## Object Declarations

Objects should always be broken across lines.

__preferred__
```js
var obj = {
  key1: 'val1',
  key2: 'val2',
  key3: {
    key4: 'val4',
    key5: 'val5'
  }
};
```

__not preferred__
```js
  var obj = { key1: 'val1', key2: 'val2', key3: { key4: 'val4', key5: 'val5' } };
```

## Golden Path

When coding with conditionals, the left hand margin of the code should be the "golden" or "happy" path.  That is, don't nest `if` statements.  Multiple return statements are OK.

__preferred__
```js
function someMethod(err, callback) {
  if (err) {
    return callback(err);
  }

  // more logic

  callback();
}
```

__not preferred__
```js
function someMethod(err, callback) {
  if (!err) {
    // more logic

    callback();
  }
}
```

__not preferred__
```js
function someMethod(err, callback) {
  if (err) {
    return callback(err);
  } else {
    // more logic
    callback();
  }
}
```


## Whitespace

Every statement (`if`, `for`, `while`, `do`, `switch`, `try`, `catch`, `finally`) should have a space before the following `{` bracket or `(` parenthese.

```js
if (x) {
  // logic
}
```

Simple arrays do not need spacing. But if there are references like the one below, then it should have spaces included.

```js
var arr = [1, 2, 3];

var arr2 = [ anotherObj[key] ];
```

Vertical white-space is needed for readability. Don't shy away from using space to make things readable.

## If Statements

All if statements should be encapsulated by `{}` brackets.

No if statements should be a single line.

__preferred__

```js
if (x === y) {
  a = 10;
} else if (x === z) {
  a = 20;
} else {
  a = 30;
}
```

__not preferred__
```js
if (x === y) a = 10;
else if (x === z) a = 20;
else a = 30;
```

__not preferred__
```js
if (x === y)
  a = 10;
else if (x === z)
  a = 20;
else
  a = 30;
```

## Try Catch

Try catch statements should follow the same rules as an if else. See the above documentation.

No function calls should be made from within a `try` (since any error within would bubble up to the `catch`)

__preferred__
```js
try {
  regionId = user.payment.region.id; // will fail if any part of dot notation is undefined
  passed = true; // will only be reached if no err
} catch(err) {
  passed = false;
}

if (!passed) {
  processUnavailableRegion(user);
} else {
  processAvailableRegion(regionId);
}
```

__not preferred__
```js
try {
  regionId = user.payment.region.id; // will fail if any part of dot notation is undefined
  processAvailableRegion(regionId); // any error in this call will bubble to the catch
} catch(err) {
  processUnavailableRegion(user);
}
```

## Use Shorthand Constructors

Do not use `new Array()` or `new Object()`. Instead, use `[]` and `{}`. This is actually more efficient, and saves a few bytes.

## Evil keywords

Do not use `eval`. It, in general, is not very safe.

Do not use `with`. It leads to some confusing situations with scope.
