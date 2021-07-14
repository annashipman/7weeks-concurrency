# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Use old box as book published 2014 so code samples
  # do not always work with up to date code
  # Xenial = 16.04
  config.vm.box = "ubuntu/xenial64"

  # Need more memory for large arrays
  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.cpus = 4
  end

  config.vm.provision "shell", inline: <<-SHELL
      apt-get update

      # Threads: Java
      apt-get install default-jdk -y
      apt-get install maven -y
      # To build and run, change into the directory of the project and:
        # mvn compile
        # mvn -q exec:java

      # Functional programming: Clojure
      # Leiningen is not in apt at 16.04
      curl -o /usr/bin/lein https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
      chmod +x /usr/bin/lein
      lein # this runs the self-install package
      # To build and run, change into the directory of the project and:
          # lein run
      # To use the interactive console:
          # lein repl
          ## NB: repl means read-evaluate-print-loop!
   SHELL
end
