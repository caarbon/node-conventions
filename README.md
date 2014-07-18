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

All names should be limited to using alpha `a-z` and numeric `0-9` characters. All names should start with an alpha character. One exception is when dealing with an outside dependency, like SQL, where a table name may contain underscores.

Variable names should be camel cased. Any constructor should start with a capital letter. Any other type of variable should start with a lowercase character.

Constants do not exist in Node. Since the idea of a frozen variable is loose. Global variables should be named like normal variables.

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

## Object Definitions

Objects should always be broken across lines.

__preferred__
```js
var obj = {
  key1: val1,
  key2: val2,
  key3: {
    key4: val4,
    key5: val5
  }
};
```

__not preferred__
```js
  var obj = { key1: val1, key2: val2 };
```

## Whitespace

Every statement (`if`, `for`, `while`, `do`, `switch`, `try`, `catch`, `finally`) should have a space before the following `{` bracket or `(` parenthese.

```js
if (x) {
  // logic
}
```

Simple arrays do not need spacing. But if an array contains complex logic, or another reference, it should have spaces included. Use your best judgement.

```js
var arr = [1, 2, 3];

var arr2 = [ anotherObj[key] ];
```

Vertical white-space is needed for readability. Don't shy away from using space to make things readable.

__preferred__
```js
var user = new User({
  id: 12
});
var userName;

user.set({
  name: {
    first: 'tim',
    last: 'marshall'
  }
});

user.sync(function() {
  userName = user.name.first + ' ' + user.name.last;

  if (user.authed) {
    isAuthed();
  } else {
    isNotAuthed();
  }
});

function isAuthed() {
  // more logic for authed users
}

function isNotAuthed() {
  // more logic for non-authed users
}
```

__not preferred__
```js
var user = new User({
  id: 12
});
var userName;
user.set({
  name: {
    first: 'tim',
    last: 'marshall'
  }
});
user.sync(function() {
  userName = user.name.first + ' ' + user.name.last;
  if (user.authed) {
    isAuthed();
  } else {
    isNotAuthed();
  }
});
function isAuthed() {
  // more logic for authed users
}
function isNotAuthed() {
  // more logic for non-authed users
}
```

## If Statements

All if statements should be encapsulated by `{}` brackets.

No if statements should be a single line.

__preferred__

```js
if (x > 10) {
  y = 1;
} else if (x > 0) {
  y = 2;
} else {
  y = 3;
}
```

__not preferred__
```js
if (x > 10) y = 1;
else if (x > 0) y = 2;
else y = 3;
```

__not preferred__
```js
if (x > 10)
  y = 1;
else if (x > 0)
  y = 2;
else
  y = 3;
```

## Try Catch

Try catch statements should follow the same rules as an if else. See the above documentation.

## Use Shorthand Constructors

Do not use `new Array()` or `new Object()`. Instead, use `[]` and `{}`. This is actually more efficient, and saves a few bytes.

## Evil keywords

Do not use `eval`. It, in general, is not very safe.

Do not use `with`. It leads to some confusing situations with scope.
