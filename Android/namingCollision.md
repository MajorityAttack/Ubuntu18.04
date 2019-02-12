### how to solve the naming collision error?

## 1 what is naming collision?
./node_modules/metro module will hash all the files' content in the project and manage these hash values as file names.
if two files are same, so the hash values of these file are same. It means maning collssion in "metro file system".

```sh
[01/23/2017, 13:17:07] <START> Building Haste Map
    Failed to build DependencyGraph: @providesModule naming collision:
      Duplicate module name: ann
      Paths: /Users/thurt/projects/example/package.json collides with /Users/thurt/projects/example/dist/esdoc/package.json

This error is caused by a @providesModule declaration with the same name across two different files.
Error: @providesModule naming collision:
  Duplicate module name: ann
  Paths: /Users/thurt/projects/example/package.json collides with /Users/thurt/projects/example/dist/esdoc/package.json
```

## 2 how to fix?

You can create a file in your project root called rn-cli.config.js with the (version specific) contents as below:
```sh
const blacklist = require('metro-config/src/defaults/blacklist');

// blacklist is a function that takes an array of regexes and combines
// them with the default blacklist to return a single regex.

module.exports = {
  resolver: {
    blacklistRE: blacklist([/dist\/.*/])
  }
};
```
## 3 At last
```sh
./gradlew assembleDebug
```

## If you build by react-native command
Have your CLI command use this config by passing the --config option:

react-native run-ios --config=rn-cli.config.js

(NB It may be a bug that you need to pass the --config argument, this location probably ought to be loaded automatically but node_modules/react-native/rn-cli.config.js takes precedence)

Be aware that your dist folder may have already been cached by the packager in which case the first time you run it you may need to reset the cache:

react-native start --config=rn-cli.config.js --resetCache

## reference:
https://stackoverflow.com/questions/41813211/how-to-make-react-native-packager-ignore-certain-directories
