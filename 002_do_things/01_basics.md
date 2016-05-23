All valid Clojure expressions are also called _forms_.

Those can be seen as the product of a simple generative grammar:

* numbers are forms: 5
* strings are forms: "hello"
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

OR and AND
==========

Logical operators works like `&&` and `||` in Javascript, working on a list of values. But be warned because __0 is not falsey__ in Clojure, but it is in ES6:

Clojure:

```
user=> (or false false 4 5)
4
user=> (or false nil 4)
4
user=> (and 2 3 4)
4
user=> (and 2 false 4)
false
user=> (and 2 nil 4)
nil


```

Javascript (I'm using Nodejs 6.1, but it should be the same in any engine):

```
> false || undefined || 4 || 5
4
> false || undefined || undefined
undefined
> 2 && 3 && 4
4
> 2 && false && 4
false
> 2 && undefined && 4
undefined
```

So, _and_ return the first falsey value or the last one of the list it they were all true, while true returns the first true-y value, or the last one otherwise.

This implies that they behave just like the logical and or or we expect, an and with a list of forms will ve falsey unless they are all true and an or will be true-y if at least one is true.
The interesting thing is that in both languages a value of the list is returned, not a simple true of false value, however that value is falsey or true-y just like the logical AND or OR or would be true or false.
