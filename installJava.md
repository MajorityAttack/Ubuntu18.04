### How to install JAVA8 binary archive on Linux?

0. Install the package from following link

```
https://www.oracle.com/technetwork/java/javase/downloads/index.html
```

1. Unzip the binary archive to any directory you wanna install java, I use `/usr/local/lib/java`

 ```
  VERSION=8u201
  DISTRO=linux-x64
  sudo mkdir /usr/local/lib/java
  sudo tar -xzvf jdk-$VERSION-$DISTRO.tar.gz -C /usr/local/lib/java 
 ```

2. Set the environment variable `~/.bashrc`, add below to the end

 ```
 # java
 JDKDIR="/usr/local/lib/java/jdk1.8.0_201"
 JREDIR=$JDKDIR/jre
 JAVA_HOME=$JDKDIR
 export PATH=$JAVA_HOME/bin:$PATH
 ```
3. Refresh profile

```
. ~/.bashrc
```

4. Test installation using

 `$ java -version`

### Notice: All diff version of jdk should be install in /usr/local/lib dir.

### If you have many version jdk to alter, the links show the detail:

```
https://www.vultr.com/docs/how-to-manually-install-java-8-on-ubuntu-16-04
```
```
https://www.digitalocean.com/community/tutorials/how-to-manually-install-oracle-java-on-a-debian-or-ubuntu-vps
```
