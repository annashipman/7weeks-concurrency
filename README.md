# Vagrant box for Seven Concurrency Models in Seven Weeks

This repo contains a Vagrantfile to run all the code examples in the book [Seven Concurrency Models in Seven Weeks](https://pragprog.com/titles/pb7con/seven-concurrency-models-in-seven-weeks/).

It also contains a Vagrantfile for another machine so that you can test distributing workloads across multiple computers. Slightly more detail in [the commit](https://github.com/annashipman/7weeks-concurrency/commit/69193a).

The code itself can be found on the [book's homepage](https://pragprog.com/titles/pb7con/seven-concurrency-models-in-seven-weeks/).

## Instructions

Each chapter has a directory which contains a README, but for ease of reference:

### Java

Chapter 2: Threads and Locks

To build and run, change into the directory of the project and:

    mvn compile
    mvn -q exec:java

### Clojure

Chapter 3: Functional Programming

Chapter 4: The Clojure Way – Separating Identity from State

To build and run, change into the directory of the project and:

    lein run

To use the interactive console:

    lein repl

### ClojureScript

Chapter 6: Communicating Sequential Processes

To compile ClojureScript:

    lein cljsbuild once

As per Clojure to run:

    lein run

### Elixir

Chapter 5: Actors

To run a script (extension .exs):

    elixir filename.exs

To run Interactive Elixir with the definitions in a file loaded:

    iex filename.ex

To run Interactive Elixir for a project with mix.exs in the root:

    iex -S mix
