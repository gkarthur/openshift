# openshift
openshift projets

## install in standlone mode

In Centos server install packages and start

```
yum install wget docker NetworkManager -y
sudo systemctl enable NetworkManager
sudo systemctl start NetworkManager
```

### install ansible 2.7 (via RPM)

wget wget https://releases.ansible.com/ansible/rpm/release/epel-7-x86_64/ansible-2.7.0-1.el7.ans.noarch.rpm

sudo yum install ansible-2.7.0-1.el7.ans.noarch.rpm

### install Openshift

Add origin repo

```
sudo wget https://storage.googleapis.com/origin-ci-test/releases/openshift/origin/master/origin.repo -O /etc/yum.repos.d/orign.repo
```

install

```
git clone https://github.com/openshift/openshift-ansible
cd openshift-ansible
sudo ansible-playbook -i inventory/hosts.localhost playbooks/prerequisites.yml
```


