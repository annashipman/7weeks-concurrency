# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Use old box as book published 2014 so code samples
  # do not always work with up to date code
  config.vm.box = "ubuntu/xenial64"

  config.vm.provision "shell", inline: <<-SHELL
      apt-get update

      # Threads: Java
      apt-get install default-jdk -y
      apt-get install maven -y
      # To To build and run, change into the directory of the project and:
        # mvn compile
        # mvn -q exec:java

   SHELL
end
