All valid Clojure expressions are also called _forms_.

Those can be seen as the product of a simple generative grammar:

* numbers are forms: 5
* strings are form: "hello"
* an operator and a list of forms inside parenthesis is a form: (+ 2 5)

whitespaces and commas can be used to separate values in forms, repeated ones are ignored. So these are all equivalents:

```
user=> (+ 1 3)
4
user=> (+,1,3)
4
user=> (+,1  3)
4
user=> (+,1 3)
4
user=> (+,,,,1, 3)
4
```
the last one is awkward but works
