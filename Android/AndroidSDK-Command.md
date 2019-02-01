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

5. To install SDK platform and tools by sdkmanager
 ```
  Android SDK Platform 28
 `$ sdkmanager "platforms;android-28"`
 
  Android SDK source 28
  `$ sdkmanager "sources;android-28"`
  
  Intel x86 Atom_64 System Image
 `$ sdkmanager "system-images;android-28;default;x86_64"`
 
  Google APIs Intel x86 Atom System Image
 `$ sdkmanager "system-images;android-28;google_apis;x86_64"`

  Android SDK Build-Tools 28.0.3 is selected
 `$ sdkmanager "build-tools;28.0.3"`
 ```
