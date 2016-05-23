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
the last one is awkward but works.

If and do
=========

`If` behave similarly to the ternary operator ` ? : `, just like the Scala ones.

So this can work:

```
user=> (if (= 5 (+ 3 2)) "it's equal!" "it's not equal")
"it's equal!"

user=> (println (if (= 5 (+ 3 2)) "it's equal!" "it's not equal"))
it's equal!
nil
```

in the second case the form prints the string and return `nil`, since nothing was returned (it's like a function returning `undefined` in Javascript when nothing was returned explicitly).

It's nice and functional but in some cases we want to perform multiple actions before returning anything, so the `do` operator comes to the rescue:

```
user=> (do (println "hello") (println "world") 42)
hello
world
42
```
the first two println are _executed_, and the last value is _returned_.
Nil behaves pretty much like Javascript `undefined`. To check that a value is Nil use the `nil?` operator. Also, nil is __falsey__, so just like in JavaScript an if or any implicit boolean conversion will treat it as a false:

```
user=> (if (println "I'm a print, don't return a thing") "this can't be!" "so, nil was falsey after all, uh?")
I'm a print, don't return a thing
"so, nil was falsey after all, uh?"
```

the print inside the if doens't return anything, so it implicitly returns a nil which is considered like a false value.
