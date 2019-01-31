### How to install Node.js via binary archive on Linux?

0. Install the package from following link

```
https://nodejs.org/en/download/
```

1. Unzip the binary archive to any directory you wanna install Node, I use `/usr/local/lib/nodejs`

 ```
  VERSION=v10.15.1
  DISTRO=linux-x64
  sudo mkdir /usr/local/lib/nodejs
  sudo tar -xJvf node-$VERSION-$DISTRO.tar.xz -C /usr/local/lib/nodejs 
  sudo mv /usr/local/lib/nodejs/node-$VERSION-$DISTRO /usr/local/lib/nodejs/node-$VERSION
 ```

2. Set the environment variable `~/.bashrc`, add below to the end

 ```
 # Nodejs
 export NODEJS_HOME=/usr/local/lib/nodejs/node-$VERSION/bin
 export PATH=$NODEJS_HOME:$PATH
 ```
3. Refresh profile

```
. ~/.bashrc
```

4. Test installation using

 `$ node -v`
 
 `$ npm version`
  
 `$ npx -v`

### To create a **sudo** link:

```
sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/node /usr/bin/node

sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npm /usr/bin/npm

sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npx /usr/bin/npx
````
