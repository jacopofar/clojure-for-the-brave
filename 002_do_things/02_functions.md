Clojure is a functional programming language: that means functions are first class citizens, and can be created, named and passed around just likenumbers, strings or symbols, exactly the same way you can in Javascript.

```clojure
user=> ((or + -) 7 5)
12
user=> ((and + -) 7 5)
```


here we take advantage of the fact that functions are by default true-y (like in Javascript or Python) and get in turn the plus and the minus operators applying them to the parameters. The inner parenthesis, then, evaluate to a function, which is in turn used as the operator. This is perfectly legal in Clojure and is the corner-stone of the various functional tricks which are the juice of LISPs.

A function can take another function as a parameter, just think about the `filter`, `map` and `reduce` functions in Python, Javascript and Scala, to name the most famous. Such functions are called "__higher order functions__".

Clojure naturally has the map operator:

```clojure
user=> (map inc [1 2 3 99])
(2 3 4 100)
```

here `inc` is a function in the standard library which does nothing but add 1 to its input; `map` applies the given function to a list of elements. It does return a list (note the round brackets instead of the squared ones).

There are two special functions: __macros__ and __special forms__. Macros will be detailed later, while special forms are structures like the if which, as we saw, can avoid evaluating some of their operands.

19.30 --

Defining a function
------------------

It's simple using the `defn` keyword

```clojure
user=> (defn triple "the triple of a number" [number] (* number 3))
#'user/triple
user=> (triple 2)
6
```

parameters go inside the square brackets. After the function name is possible to define an optional short description, which is a way to document the code embeded in the language itself. So from the repl we can see the description:

```clojure
user=> (doc triple)
-------------------------
user/triple
([number])
  the triple of a number
nil
```

and it's possible to define multiple arity functions

```clojure
user=> (defn triple "the triple of nothing is zero" [] 0)
#'user/triple
user=> (triple)
0
```

functions are identified by their arity, not by the argument type, and it's possible to define a variable-arity function using rest parameters with a `&`:

```clojure
user=> (defn triple "the triple of nothing is zero" [number & other_numbers] (str (* number 3) " ignoring these: " (clojure.string/join ", "other_numbers)))
#'user/triple
user=> (triple 5 6 78 9)
"15 ignoring these: 6, 78, 9"
```

this is similar to how overloading works in Java, except for the fact you can't tell arguments by their type but only from the arity. Javascript on the other hand has no explicit function overload.

Destructuring
-------------
TODO continue
