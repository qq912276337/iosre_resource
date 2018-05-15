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
* 查看进程信息：ps -e | grep /Applications/
* /opt/theos/bin/nic.pl
* scp /Users/snakeninny/Code/dumpdecrypted/dumpdecrypted.dylib root@192.168.0.102:/var/mobile/Containers/Data/Application/4D7DB427-2F3D-4686-B1EA-229C9AD0C12D/Documents/

### Cycript
* cycript -p MobileNotes -> ?expand -> [[UIApp keyWindow] recursiveDescription] -> [#0x175ee3e0 nextResponder]
* [[NSFileManager defaultManager] URLsForDirectory:NSDocumentDirectory inDomains:NSUserDomainMask][0] -> scp /Users/snakeninny/Code/dumpdecrypted/dumpdecrypted.dylib root@iOSIP:/var/mobile/Containers/Data/Application/D41C4343- 63AA-4BFF-904B-2146128611EE/Documents/ -> DYLD_INSERT_LIBRARIES=/path/to/dumpdecrypted.dylib /path/to/executable

### LLDB

* 启动进程：debugserver -x backboard IP:port /path/to/executable

* 附加进程：debugserver IP:port -a "ProcessName"
* debugserver *:1234 -a "MobileNotes"* lldb -> process connect connect://192.168.0.102:1234
* image list -o -f
* 设置断点：br s -a '0x000b2000+0x3dce0'
* 使用-n根据方法名设置断点：：breakpoint set -n viewWillAppear:
* 使用-f指定文件：breakpoint set -f ViewController.m -n viewDidLoad
* 使用-l指定文件某一行设置断点：breakpoint set -f ViewController.m -l 38
* 使用-c设置条件断点e.g: text:方法接受一个ret的参数，我们想让ret == YES的时候程序中断：breakpoint set -n text: -c ret == YES
* crash的时候，使用thread backtrace查看堆栈调用 （简写bt）
* thread return NO 直接返回值NO
### dyld

* ~/dsc_extractor/dyld-210.2.3/launch-cache/dsc_extractor  /Users/snakeninny/Code/dyld/dyld_shared_cache_armv7 /Users/snakeninny/Code/dyld/demo
* 