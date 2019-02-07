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
