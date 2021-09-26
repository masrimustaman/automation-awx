# Install and configure Ansible AWX

### Set up the repository
```
 sudo yum install -y yum-utils
 
 sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo

```

### Install Docker
```
sudo dnf install docker-ce
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER

# sudo pip3 install docker-compose #old_way
python3 -m pip install docker-compose
sudo alternatives --set python /usr/bin/python3 #to set python3 as python
```

### Install AWX
```
sudo dnf install git -y 
python3 -m pip install awxkit
python3 -m pip install sphinx sphinxcontrib-autoprogram

wget https://codeload.github.com/ansible/awx/zip/refs/tags/17.1.0
sudo dnf install unzip -y
unzip 17.1.0
awx-17.1.0/
cd installer/
openssl rand -base64 30 # generate secret encryption key # FdEado2byqSmDfOXfO8bYAkyc7p258dFacDqh48r

#edit inventory file
#secret_key=FdEado2byqSmDfOXfO8bYAkyc7p258dFacDqh48r
#admin_user=admin
#admin_password=password

ansible-playbook -i inventory install.yml
```

### Verify
`ss -tulpn`

```
Netid            State              Recv-Q             Send-Q                         Local Address:Port                         Peer Address:Port                 
tcp              LISTEN             0                  128                                  0.0.0.0:80                                0.0.0.0:*      
```


### Other setting
1. Upgraded the ram to 4GB and cpu to 4 vcpu
2. port forwarding 80 to 8080
