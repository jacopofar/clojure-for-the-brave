The command `lein new app clojure-noob` generated this folder structure. It already contains a functioning Hello world program along with its namespace.

The .clj files are identified as ASCII text by Mac OS X file command

Leiningen also creates a project.clj file in the project root with the project metadata.

Interestingly, it also generates documentation and test stubs and the .gitignore and .hgignore files.

Another cool thing is that `lein uberjar` generates an executable JAR of the project with no further plugins needed, both a standalone and a Clojure-requiring one.

The Clojure REPL runs in the context of the current directory (like Nodejs's), so it's posible to run the `(-main)` function of the progra function of the programm
