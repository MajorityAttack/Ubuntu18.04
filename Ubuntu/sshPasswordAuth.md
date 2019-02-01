#To Access system from outside GCP
```sh
 $ su - root
 $  ll /etc/ssh/sshd_config
 $ vim /etc/ssh/sshd_config
 PasswordAuthentication yes
 $ service sshd restart
```
