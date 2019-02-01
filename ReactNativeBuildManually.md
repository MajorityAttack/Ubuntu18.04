# How to manually build react-native projects with gradle 

##  1. creat react-native project
```sh
 $ react-native init AwesomeProject
```

##  2. build react-native with many nbi versions
```sh
 $ cd AwesomeProject
 
 adapt the app/build.gradle file
 $ vim app/build.gradle
 def enableSeparateBuildPerCPUArchitecture = true
 
 $ ./gradlew assembleDebug
```

##  3. install apk on emulator
```sh
  copy the apk to the target machine
  $ emulator -list-avds
  $ emulator -avd Nexus_6_API_27
  $ adb install app-x86-debug.apk
```

##  4. error occure
"unable to load script from assets 'index.android.bundle'"
 <img src="https://user-images.githubusercontent.com/13952270/35189113-fd583f76-fdf8-11e7-937e-b03d8bd13a37.png" width="300">
 
##  5. To fix this error
```
Go to your project directory and check if this folder exists android/app/src/main/assets
i) If it exists then delete two files viz index.android.bundle and index.android.bundle.meta
ii) If the folder assets doesn't exist then create the assets directory there.
From your root project directory do
cd android && ./gradlew clean
Finally, navigate back to the root directory and check if there is one single entry file called index.js
i) If there is only one file i.e. index.js then run following command
react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
ii) If there are two files i.e index.android.js and index.ios.js then run this
react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
```
##  6. build and run the apk (reference 2,3 step)
## Now you can successfully to build react native project manunally.
