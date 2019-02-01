### How to add git submodule in github?

Add protobuf 3.6.x branch as submodule helloworld project

 ```
 cd helloworld
 git submodule add -b 3.6.x https://github.com/google/protobuf.git Protobuf
 ```
 protobuf info will showed in the .gitmodules file

 ```
 git submodule init
 ```
 ```
git add protobuf
```
```
git commit -m "init protobuf submodules"
```
```
git push origin master
```
## protobuf module will showed in the github
