<h3>Hortonworks HDF Config for Vagrant Virtualbox</h3>
<br>
<br>Run the following commands to initialize and start vagrant:
<br>
```
<br>vagrant init
<br>vagrant box add hashicorp/precise64 #Select Virtualbox
<br>vi Vagrantfile
<br>:%s/# config.vm.network "forwarded_port", guest: 80, host: 8080/config.vm.network "forwarded_port", guest: 80, host: 8080\r   config.vm.network "forwarded_port", guest: 8080, host: 18080\r   config.vm.network "forwarded_port", guest: 9090, host: 19090\r   #EndPortForwarding
<br>:x
<br>vagrant up
```
