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

__good__
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

__bad__
```js
var x = 12 // !!!
var y = function() {} // !!!

for (var i = 0, l = 5; i < l; i++) {
  // something
}; // !!!

function handler() {
  // something
  return // !!!
}; // !!!

; // !!!
```

## Naming

All names should be limited to using alpha `a-z` and numeric `0-9` characters. All names should start with an alpha character. One exception is when dealing with an outside dependency, like SQL, where a table name may contain underscores.

Variable names should be camel cased. Any constructor should start with a capital letter. Any other type of variable should start with a lowercase character.

Constants do not exist in Node. Since the idea of a frozen variable is loose. Global variables should be named like normal variables.

__good__
```js
var defaultValue3 = 30;

function Parent() {
  this.myValue1 = 10;
  this.myValue2 = 20;
  this.myValue3 = defaultValue3;
}
var child = new Parent();
```

__bad__
```js
var DEFAULTVALUE3 = 30; // !!!

function parent() { // !!!
  this.MyValue1 = 10; // !!!
  this.myvalue2 = 20; // !!!
  this.my_value_3 = 30; // !!!
}
var Child = new Parent(); // !!!
```

## Objects

Objects should always be broken across lines.

__good__
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

__bad__
```js
  var obj = { key1: val1, key2: val2 };
```
