# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Use old box as book published 2014 so code samples
  # do not always work with up to date code
  # Xenial = 16.04
  config.vm.box = "ubuntu/xenial64"
  config.vm.hostname = "7weeks-concurrency-vagrantbox"


  # Need more memory for large arrays
  config.vm.provider :virtualbox do |v|
    v.memory = 4096
    v.cpus = 4
  end

  config.vm.provision "shell", inline: <<-SHELL
      apt-get update

      # Java
      apt-get install default-jdk -y
      apt-get install maven -y

      # Clojure and ClojureScript
      # Leiningen is not in apt at 16.04
      curl -o /usr/bin/lein https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
      chmod +x /usr/bin/lein
      # The first time you use lein it will run the self-install package
      # So you need internet access even while using the box
      # Annoying. TODO. Fixes welcome.

      # Elixir
      wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb && sudo dpkg -i erlang-solutions_2.0_all.deb
      apt-get update
      apt-get install esl-erlang -y
      apt-get install elixir -y

      # OpenCL
      apt-get install build-essential -y # make, gcc and other tools
      apt-get install ocl-icd-opencl-dev -y

      # Hadoop
      wget https://dlcdn.apache.org/hadoop/common/hadoop-2.10.1/hadoop-2.10.1.tar.gz
      tar -xzvf hadoop-2.10.1.tar.gz
      mv hadoop-2.10.1 /usr/local/hadoop
      # Need to set Java Home before using
      # Set it to dynamically read what the Java Home is
      sed -i 's/export JAVA_HOME=${JAVA_HOME}/export JAVA_HOME=$(readlink -f \\/usr\\/bin\\/java | sed "s:bin\\/java::")/g' /usr/local/hadoop/etc/hadoop/hadoop-env.sh
      # Alias it to hadoop
      echo "alias hadoop=\"/usr/local/hadoop/bin/hadoop\"" >> /home/vagrant/.bashrc
   SHELL

   # Make vagrant accessible from the public network
   # To find out what bridging to use, you can run this without the second clause below, and then
   # Vagrant will prompt with a list of possible bridges
   config.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
end
