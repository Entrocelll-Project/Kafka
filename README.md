# Kafka
Installing Kafka on Google Cloud and Creating Kafka Topics
-First we create a google cloud account-



![image](https://github.com/Entrocelll-Project/Kafka/assets/122750012/705899c3-1f62-46b0-935d-a05dad494444)
-Click the compute engine button and then open the vm instances section.-
Create new ınstance



![image](https://github.com/Entrocelll-Project/Kafka/assets/122750012/ca17d3a3-65d5-4ffa-a360-408a8092c6c5)


-After the VM is installed, it will be listed. Let's run our machine by clicking on the ssh button as in the photo.-


![image](https://github.com/Entrocelll-Project/Kafka/assets/122750012/6a1b1599-e2a3-4fdf-8fcf-136004ed8560)


-Then we install Docker on our system. You must have an account on Docker Hub.-

 *sudo yum update -y
 
 *sudo yum install docker
 
 *sudo systemctl start docker 
 
 *sudo systemctl enable docker

 
 -We finished the Docker installation and logged in with the docker hub account name and password. Now we will install Kafka and take a kafka image.-

 
 *docker run -d --name kafka -p 9092:9092 docker.io/ubuntu/kafka
 
 -Zookeeper installation-
 
 *docker run --name kafka -d -p "9092:9092" -e KAFKA_ADVERTISED_HOST_NAME=192.168.99.100 --link zookeeper:zookeeper ches/kafka
 
 *sudo docker pull ches/kafka

 *sudo docker network create kafka-net
 
 *docker run -d --name zookeeper --network kafka-net zookeeper:3.4

 
 -Until this stage, we first created a virtual machine on Google Cloud and installed Docker on this machine. We also installed Kafka via Docker. We also downloaded our zookeeper application, which is required for Kafka. Finally, the process of creating a Kafka topic remains.-

 
 *sudo docker run --rm --network kafka-net ches/kafka \
 
  kafka-topics.sh --create --topic test --replication-factor 1 --partitions 1 --zookeeper zookeeper:2181
Created topic "test"

-We created a topic called test-



![image](https://github.com/Entrocelll-Project/Kafka/assets/122750012/62ae41a7-b006-43fc-9bfe-59de78ce6a22)
