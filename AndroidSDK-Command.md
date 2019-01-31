### How to install Android SDK on Linux?

0. Install the package from following link

```
https://developer.android.com/studio/#downloads
```

1. Unzip the binary archive to any directory you wanna install SDK, I use `$HOME/android_sdk`

 ```
  mkdir $HOME/android_sdk
  cd $HOME/android_sdk
  unzip ~/download/sdk-tools-linux-4333796.zip
 ```

2. Set the environment variable `~/.bashrc`, add below to the end

 ```
 # Android
 export ANDROID_HOME=$HOME/android_sdk
 export PATH=$PATH:$ANDROID_HOME/tools
 export PATH=$PATH:$ANDROID_HOME/tools/bin
 ```
3. Refresh profile

```
. ~/.bashrc
```

4. Test installation using

 `$ android`

### Notice: All diff version of jdk should be install in /usr/local/lib dir.

### If you have many version jdk to alter, the links show the detail:

