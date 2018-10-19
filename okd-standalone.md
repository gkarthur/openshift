# Install OKD on standlone mode

## create EC2 instance

Search and select Centos in instances repository
Select t2.large for the test purpose
Lanch instance

## install OKD

connect with ssh key on ec2 instance, and run following command

```
$ sudo yum update -y
$ sudo yum install git -y
$ git clone https://github.com/gshipley/installcentos.git
$ cd installcentos
$ sudo ./install-openshift.sh
Domain to use: (18.221.144.190.nip.io): ec2-18-221-144-190.us-east-2.compute.amazonaws.com
Username: (root): origin
Password: (password): origin
OpenShift Version: (3.10):
IP: (172.31.19.171):
API Port: (8443):

...

* Your console is https://console.ec2-18-221-144-190.us-east-2.compute.amazonaws.com:8443
* Your username is origin
* Your password is origin
*
* Login using:
*
$ oc login -u origin -p origin https://console.ec2-18-221-144-190.us-east-2.compute.amazonaws.com:8443/
******
Login successful.
```

## OKD with OC cluster up

### installation

```
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-server-v3.11.0-0cbc58b-linux-64bit.tar.gz
tar -xvf openshift-origin-server-v3.11.0-0cbc58b-linux-64bit.tar.gz
mv openshift-origin-server-v3.11.0-0cbc58b-linux-64bit openshift 
```

### configuration

Modify file /etc/docker/daemon.json with content below, then restart Docker

```
{
  "insecure-registries" : ["172.30.0.0/16"]
}
```

Restart docker service

```
sudo systemctl restart docker
```

### start server

```
cd openshiftt
sudo ./oc cluster up --public-hostname=$(hostname)
```

### Create application

sudo ./oc login -u system:admin
sudo ./oc get all
sudo ./oc new-app --name=mytest wildfly:latest~https://github.com/Preeticp/os-sample-java-web


### stop server

```
cd openshiftt
sudo ./oc cluster down
```



