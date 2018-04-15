#  iOS逆向

## 命令集

### 未知

* class-dump头文件： class-dump -H /Applications/Calculator.app -o ./h
* ./TheosScript.sh
* 查看是否加密：otool -arch armv7 -l WeChat.decrypted | grep crypt
* 局域网下链接ios-ssh：ssh root@192.168.0.102
* ls -l /Library/ | grep RHRevealLoader
* 从ios设备scp到电脑: scp root@192.168.0.102:~/Containers/ /Users/snakeninny/Code
* lipo -info libcycript-sim.dylib 
	--> Architectures in the fat file: libcycript-sim.dylib are: i386 x86_64 

### LLDB

* 

### dyld

* ~/dsc_extractor/dyld-210.2.3/launch-cache/dsc_extractor  /Users/snakeninny/Code/dyld/dyld_shared_cache_armv7 /Users/snakeninny/Code/dyld/demo
* 