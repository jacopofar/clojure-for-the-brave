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
