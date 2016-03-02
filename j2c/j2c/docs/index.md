`j2c` is a CSS preprocessor working from JavaScript objects and arrays. By default, it **generates local class and animation names** so that you can ship CSS with your components without risking name clashes in the .

You get most of the advantages of SASS, LESS or Stylus, like **mixins** and **nested selectors and at-rules**, in a 1KB† package.

*† minified and gzipped.*

Great match for client-side **MV\* frameworks** and **isomorphic apps**.

Here's a quick taste for the library:

```
$ npm install --save j2c
```

Then:

```JavaScript
j2c = require('j2c') 
mysheet = j2c.sheet({
  ".foo": {
    color: "red",
    "@media  (min-width:48.01em)": {
      color: "green"
    },
    "& .bar, & .baz": {
      text_decoration: "underline"
    }
  }
})
```

```CSS
.foo_j2c_9k7w_0 .bar_j2c_9k7w_0,.foo_j2c_9k7w_0 .baz_j2c_9k7w_0{
    text-decoration:underline;
}
.foo_j2c_9k7wpv1qfbmbwef8tel3edl_0{
    color:red;
}
@media  (min-width:48.01em){
    .foo_j2c_9k7wpv1qfbmbwef8tel3edl_0{
        color:green;
    }
}
```

`mysheet.foo` will return  a `'foo_j2c_xxxx_n'` string (where `xxxx` is acually longer, it is truncated here for readability), ready to use as a class in templates. `<style>{mysheet}</style>` in your template will insert the sheet in the DOM in modern browsers (IE9+). Other methods are available for older IE versions.



#documentation.md

You

me

us.

Thanks a lot for the feedback. The code samples are basically a product showcase, yes.