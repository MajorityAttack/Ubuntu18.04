# How to add new user on ubuntu 18.04 system in GCP

##  1. add user on ubuntu 18.04
```sh
 $ [sudo]  adduser UserName
```

##  2. add the user to root and admin group
```sh
 $ [sudo]  usermod -aG sudo UserName
 $ [sudo]  usermod -aG admin UserName
```

##  3. Access system from outside GCP
```sh
 $ su - root
 $  ll /etc/ssh/sshd_config
 $ vim /etc/ssh/sshd_config
 PasswordAuthentication yes
 $ service sshd restart
```
## Now you can access the system from GCP outside
