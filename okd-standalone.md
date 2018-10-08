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







