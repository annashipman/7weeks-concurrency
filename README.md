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

Chapter 7: Data Parallelism

To build and run, change into the directory of the project and:

  ./run

### Clojure

Chapter 3: Functional Programming

Chapter 4: The Clojure Way – Separating Identity from State

To build and run, change into the directory of the project and:

    lein run

To use the interactive console:

    lein repl

**Note: Not all Clojure examples work as they should. For more information, read my blog post: [Why didn't Clojure work concurrently in Vagrant?](https://www.annashipman.co.uk/jfdi/clojure-vagrant.html)**

### ClojureScript

Chapter 6: Communicating Sequential Processes

To compile ClojureScript:

    lein cljsbuild once

As per Clojure to run:

    lein run

The server is then running at `http://7weeks-concurrency-vagrantbox.lan:3000`.

### Elixir

Chapter 5: Actors

To run a script (extension .exs):

    elixir filename.exs

To run Interactive Elixir with the definitions in a file loaded:

    iex filename.ex

To run Interactive Elixir for a project with mix.exs in the root:

    iex -S mix

### OpenCL

Chapter 7: Data Parallelism

To build, change into the directory of the project and:

    make
    ./target/<executable-name>

(`make` gives a warning which I have ignored and it seems to be working.)

The Ripple and Zoom examples are written in Java and compiled with Maven, see above.

### Hadoop

Chapter 8: The Lambda Architecture

To run Hadoop locally, change into the directory of the project and:

    hadoop jar target/<projectname>-1.0-jar-with-dependencies.jar input output

To run a Hadoop cluster, following the examples in the book, you need an AWS account with the AWS and EMR tools installed. I've not set up any of that; instructions are in the book.
