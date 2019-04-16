infrastruture part
=====================
install docker on ubuntu
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
apt-cache policy docker-ce
sudo apt-get install -y docker-ce
sudo systemctl status docker
sudo groupadd docker
sudo usermod -aG docker $USER
docker run hello-world
groups(need root to reflect the new group)
docker info
```

1. manually configuration:docker install[[1]](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and use without root[[2]](https://docs.docker.com/install/linux/linux-postinstall/) on 16.04 for microservice(need create ansible script for this)
2. containerlize microservice and hit the route inside container(expose docker container port correctly [[3]](https://stackoverflow.com/questions/33379393/docker-env-vs-run-export)
3. build the image, run container and test external incoming traffic(change security group would be needed on instance)
[[4]](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html) could hit microservice route
ToDo
4. create ecr repo first(aws cli config) 
[[5]](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html#cli-quick-configuration) then register the created image[[6]](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-basics.html)
5. create deployment for a pod with 3 instances[[7]](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)(or something other object which specify the service availability) by refering the registered image
6. expose pod as kubernetes service ?





