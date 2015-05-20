一、USB调试
即可ssh到iOS中。
使用场景举例
完全脱离WiFi，使用USB连接到iOS，用lldb调试SpringBoard。
i) 把本地2222端口转发到iOS的22端口
/Users/snakeninny/Code/USBSSH/tcprelay.py -t 22:2222

ii) ssh过去并用debugserver attach到SpringBoard

ssh root@localhost -p 2222
debugserver *:1234 -a "SpringBoard"
iii) 把本地1234端口转发到iOS的1234端口

/Users/snakeninny/Code/USBSSH/tcprelay.py -t 1234:1234
iv) 用lldb开始调试

lldb
process connect connect://localhost:1234

直接复制：
1、
/Users/mac/Desktop/LLDB/usbmuxd/tcprelay.py -t 22:2222
2、
ssh root@localhost -p 2222
3、
debugserver *:1234 -a "SpringBoard"
4、
/Users/mac/Desktop/LLDB/usbmuxd/tcprelay.py -t 1234:1234
5、
lldb
process connect connect://localhost:1234


二、WIFI调试


三、cycript的附加
1.ssh root@192.168.0.100
2.ps -e | grep /Applications
3.cycript -p 2902
4.[[UIApp keyWindow] recursiveDescription]

[#0x16968a00 nextResponder]

description

四、获取类名的实现文件
grep -r UIBarButtonItem /System/Library/
grep -r UIBarButtonItem /Applications/
grep -r UIBarButtonItem /Applications/Preferences.app/

五、打印16进制的数
(lldb) p/x a