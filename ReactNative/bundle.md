### What does "bundle" mean in the react native ??
```sh
 * The react.gradle file registers a task for each build variant (e.g. bundleDebugJsAndAssets and bundleReleaseJsAndAssets).
 * These basically call `react-native bundle` with the correct arguments during the Android build
 * cycle. By default, bundleDebugJsAndAssets is skipped, as in debug/dev mode we prefer to load the
 * bundle directly from the development server. 
 
 * The bundle is loaded from local development server, after react-native run-android running.
 * But if you build project with gradle, you should configration build.gradle file to add bundle to build.
```
## The configuration info
```sh
project.ext.react = [
    // the root of your project, i.e. where "package.json" lives
    root: "../../",

    // the entry file for bundle generation
    entryFile: "index.js",

    // whether to bundle JS and assets in debug mode
    // to bundle JS and ssset with ./gradlew assembleDebug
    bundleInDebug: true,

    // whether to bundle JS and assets in release mode
    // Notice: the bundle is opened in Release mode, There is no need to set it with true. !!!!!
    // When ./gradlew assembleRelease issued, the  Task :app:bundleReleaseJsAndAssets is include defaultly.
    // bundleInRelease: true,

    // by default the gradle tasks are skipped if none of the JS files or assets change; this means
    // that we don't look at files in android/ or ios/ to determine whether the tasks are up to
    // date; if you have any other folders that you want to ignore for performance reasons (gradle
    // indexes the entire tree), add them here. Alternatively, if you have JS files in android/
    // for example, you might want to remove it from here.
    //inputExcludes: ["third_party/**", "ios/**"],
    inputExcludes: ["android/**", "ios/**", "third_party/**"],

]
```

```sh
react-native bundle --platform android --dev false --entry-file index.js --bundle-output ?? --assets-dest ??

`--dev` - a boolean with a default value of `true`. With the `--dev true` flag in "Debug" mode (./gradlew assembleDebug), 
the bundled JavaScript code turns on useful development warnings and limits performance optimizations. 
For production it is recommended to pass `--dev false`. 
Also for production, be sure to have your native build configuration set to `Release` 
(e.g., Xcode's Release configuration for iOS and gradle's `assembleRelease` task for Android) 
in order to disable things like the shake-to-show developer menu.
```

reference:
app/build.gradle
node_modules/react-native/react.gradle

https://github.com/facebook/react-native/pull/4299/commits/d92b3b3e9b453231853f0440c37514d02252d70f
https://github.com/facebook/react-native/issues/4181
