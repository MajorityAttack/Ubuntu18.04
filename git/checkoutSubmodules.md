### How to check git submodule recursively in github?

 Method 1:

 ```
 git clone --recursive https://github.com/majorityattack/helloworld.git

 ```
 
 Method 2:
 ```
 git clone https://github.com/majorityattack/helloworld.git
 cd helloworld
 git submodule update --init --recursive
 
 (If submodules have been inited, please using following)
 git submodule update --recursive
 ```  
 
 Notice:
 ```
 If you want to check source code step by setp, please following these command:
 
 git clone https://github.com/majorityattack/helloworld.git
 cd helloworld
 git submodule update --init 
 //gRPC and protobuf source code will be downloaded, but not including the third_party in gRPC and protobuf
 
 cd gRPC
 git submodule update --init
 //the sudmodule source code of gRPC will be downloaded, but not including the third_party of gRPC modules'
 ```  
