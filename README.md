# IClojure

An Interactive Clojure repl, inspired by IPython.

[![Build Status](https://travis-ci.org/cosmin/IClojure.png?branch=master)](https://travis-ci.org/cosmin/IClojure)

## Getting started

### Standalone

The simplest way to start with IClojure is to download the latest standalone IClojure jar

```
curl -O -L http://clk.tc/iclojure-latest.jar
java -jar iclojure-latest.jar
```

Alternatively, you can download the following script, mark it executable and put it somewhere in path

```
curl -O https://raw.github.com/cosmin/IClojure/master/bin/iclojure
chmod +x iclojure
sudo mv iclojure /usr/local/bin
```

Then you can simply launch `iclojure` at any time.

### Leiningen

If you are already using Leiningen the simplest way to get started with IClojure is to use the `lein-iclojure` plugin.

### Leiningen 1.x

```
lein plugin install lein-iclojure 1.1
```

### Leiningen 2

Add `[lein-iclojure "1.1"]` to the `:user` profile in `~/.lein/profiles.clj`. Here is an example

```clojure
{:user {:plugins [ [lein-iclojure "1.1"] ]}}
```

### Maven

If you are already using the latest `clojure-maven-plugin` snapshot you can simply add IClojure to your dependencies

```
<dependency>
  <groupId>org.offbytwo.iclojure</groupId>
  <artifactId>iclojure</artifactId>
  <version>1.1.1</version>
</dependency>
```

and then IClojure will replace the usual repl

```
mvn clojure:repl
```

## Development

IClojure ships with the latest alpha of Clojure 1.4, although it supports Clojure >= 1.2

```
git checkout https://github.com/cosmin/IClojure
cd IClojure
bin/run.sh
```

## Package

You can package IClojure for distribution, including sources and a standalone jar with

```
mvn clean package
```

The `iclojure-*-standalone.jar` is a self-contained Jar that includes all the necessary dependencies.

## Features

- Tab completion
- Shorthand for source and doc
- Shorthand for introspecting Java objects and classes via reflection
- Proper Control-C handling, although not very portable
- persist history across sessions to ~/.iclojure_history
- input and output caching of last 1000 elements

## Tab completion

- variable
- method invocations
- "(.method" completion for all java methods for any of the classes in the current namespace
- "(. object method" completion for all the methods of the object (or a form that evaluates to an object)
- namespaces
- java classes
- import statements for both symbols and import lists

## Input / output caching

In addition to the Clojure convention of caching the last 3 output in `*1`, `*2` and `*3` IClojure also caches the last 1000 input and output

```
(input 102) ; => returns the input from line 102
(output 102) ; => returns the output from line 102
```

## Other shorthands

```
    ?symbol          => (doc symbol)
    ??symbol         => (source symbol)
    %d symbol        => show constructors, methods and fields of the given object or Class
    %f class         => find all classes matching this name (supports globs)
    %f class package => like the above, but restrict search to the given package
```

## Roadmap

- tab completion for require and use forms
- abort long runing tasks with Ctrl+C
- launch editor from within IClojure

## License

Copyright (C) 2012 Cosmin Stejerean

Distributed under the Eclipse Public License, the same as Clojure.
