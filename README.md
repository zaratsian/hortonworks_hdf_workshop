<h3>Hortonworks HDF Config for Vagrant Virtualbox</h3>
<br>
<br>Run the following commands to initialize and start vagrant:
```
vagrant init
vagrant box add hashicorp/precise64 #Select Virtualbox
vi Vagrantfile
:%s/config.vm.box = "base"/config.vm.box = "hashicorp\/precise64"
:%s/# config.vm.network "forwarded_port", guest: 80, host: 8080/config.vm.network "forwarded_port", guest: 80, host: 8080\r  config.vm.network "forwarded_port", guest: 8080, host: 18080\r  config.vm.network "forwarded_port", guest: 9090, host: 19090\r  #EndPortForwarding
:x
vagrant up
vagrant ssh
```
<br>Update and Install JDK:
```
sudo apt-get update
sudo apt-get install openjdk-7-jre
```
<br>Install NiFi:
```
wget wget https://archive.apache.org/dist/nifi/0.7.0/nifi-0.7.0-bin.tar.gz
tar xvf nifi-0.7.0-bin.tar.gz
```
<br>Install Zookeeper:
```
sudo apt-get install zookeeperd
```
<br>Install Kafka:
```
wget "http://mirror.cc.columbia.edu/pub/software/apache/kafka/0.10.0.0/kafka_2.10-0.10.0.0.tgz"
tar xvf kafka_2.10-0.10.0.0.tgz
# Change memory
```
<br>Install Storm:
```
wget http://www-us.apache.org/dist/storm/apache-storm-1.0.2/apache-storm-1.0.2.tar.gz
tar xvf apache-storm-1.0.2.tar.gz
```
<br>Startup Services (Nifi, Kafka, Storm):
```
echo "[ INFO ] Starting NiFi on local port 8080 (18080)
~/nifi-0.7.0/bin/nifi.sh start
echo "[ INFO ] Starting Kafka on port 9092"
nohup ~/kafka_2.10-0.10.0.0/bin/kafka-server-start.sh ~/kafka_2.10-0.10.0.0/config/server.properties
```
