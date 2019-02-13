### How to release android apk?

0. Generating a signing key

```
$ keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```
This command prompts you for passwords for the keystore and key and for the Distinguished Name fields for your key. 
It then generates the keystore as a file called my-release-key.keystore.

1. Setting up gradle variables
Place the my-release-key.keystore file under the android/app directory in your project folder.
Edit the file ~/.gradle/gradle.properties or android/gradle.properties, 
and add the following (replace ***** with the correct keystore password, alias and key password)
 ```sh
 MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
 MYAPP_RELEASE_KEY_ALIAS=my-key-alias
 MYAPP_RELEASE_STORE_PASSWORD=*****
 MYAPP_RELEASE_KEY_PASSWORD=*****
 ```

2. Adding signing config to your app's gradle config
Edit the file android/app/build.gradle in your project folder, and add the signing config,

 ```
...
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
                storeFile file(MYAPP_RELEASE_STORE_FILE)
                storePassword MYAPP_RELEASE_STORE_PASSWORD
                keyAlias MYAPP_RELEASE_KEY_ALIAS
                keyPassword MYAPP_RELEASE_KEY_PASSWORD
            }
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
...
 ```
3. Generating the release APK

```sh
$ cd android
$ ./gradlew assembleRelease
```

Reference:
https://facebook.github.io/react-native/docs/signed-apk-android
