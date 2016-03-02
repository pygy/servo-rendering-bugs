# `j2c.inline()`

`j2c.inline()` is meant to generate inline stlyes.


```JavaScript
j2c.inline({
  background_color:"red",
  border: [
    "1px solid grey",
    {left_width: "3px"}
  ]
})
```

```CSS
background-color:red;
border:1px solid grey;
border-left-width:3px;
```

# Ordering rulesets and properties.

Source objects passed to `j2c` can hold keys that are either properties, selectors or at-rules. They will end up in the CSS output in the following order:

- (sub-)selectors
- properties
- at-rules

Within each of these categories, the source/insertion order is respected, provided no key was deleted and re-inserted.

The ES5 standard says that iteration order using `for(key in object)` is undefined and left to the implementers. In practice, however, as long as a few rules are respected, we can rely on the fact that the iteration order is identical to the insertion order. This holds as long as:

- there are no unsigned integer keys (even in textual form, so no `5` nor `"5"`)
- no keys are `delete`d and inserted back.
- the object's prototype chain doesn't contain any iterable entry†.

The JS objects that `j2c` manipulates don't have any integer-like keys, and it will thus respect the source order in the outpu

If you feel paranoid about this, or if you do weird things with your source objects, you can get a guaranteed predictable property order by using arrays.

`j2c.sheet({".foo": [{bar: 3}, {baz: 4}]})` will always have `bar` before `baz`.

†: This condition may not be necessary, but I didn't test it and would recommend not to rely on it unless you test it extensively and find out it works predictably.

function Foo() {this.foo=5;this.bar=6}
Foo.prototype={buz:1,damptil:2}

f = new Foo()
for (n in f) {console.log(n)};
