# openshift
openshift projets

## install in standlone monde

In Centos server

yum install wget docker NetworkManager -y

### install ansible 2.7 (via RPM)

wget wget https://releases.ansible.com/ansible/rpm/release/epel-7-x86_64/ansible-2.7.0-1.el7.ans.noarch.rpm

sudo yum install ansible-2.7.0-1.el7.ans.noarch.rpm

### install Openshift

git clone https://github.com/openshift/openshift-ansible
cd openshift-ansible
sudo ansible-playbook -i inventory/hosts.localhost playbooks/prerequisites.yml
