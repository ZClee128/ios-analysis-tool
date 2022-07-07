## iosbug解析包

```oc
奔溃日志
此处删除了部分内容
Code Type:           ARM-64 (Native)  注意这里！！！
Role:                Foreground
Parent Process:      launchd [1]
Coalition:           com.gomemyc.mylc.ios.enterprise.CrashTest [651]


Date/Time:           2017-11-13 18:20:06.3615 +0800
Launch Time:         2017-11-13 18:20:04.7860 +0800
OS Version:          iPhone OS 11.0.3 (15A432)
Baseband Version:    6.17.00
Report Version:      104

Exception Type:  EXC_CRASH (SIGABRT)
Exception Codes: 0x0000000000000000, 0x0000000000000000
Exception Note:  EXC_CORPSE_NOTIFY
Triggered by Thread:  0

Application Specific Information:
abort() called

Filtered syslog:
None found

Last Exception Backtrace:
0   CoreFoundation                  0x183c2bd38 __exceptionPreprocess + 124
1   libobjc.A.dylib                 0x183140528 objc_exception_throw + 55
2   CoreFoundation                  0x183bc4c44 _CFThrowFormattedException + 111
3   CoreFoundation                  0x183c738cc -[__NSArrayI objectAtIndexedSubscript:] + 131
4   CrashTest                       0x100537b28 0x100530000 + 31528
5   CrashTest                       0x100537a60 0x100530000 + 31328
6   UIKit                           0x18d07020c -[UIApplication sendAction:to:from:forEvent:] + 95
7   UIKit                           0x18d07018c -[UIControl sendAction:to:forEvent:] + 79
8   UIKit                           0x18d05af4c -[UIControl _sendActionsForEvents:withEvent:] + 439

此处删除了部分内容
```
```
可以看到 Last Exception Backtrace: 下面有我们 APP 崩溃的两条信息。0x100530000 是基址，0x100537b28 和 0x100537a60 是调用堆栈的地址，后面会用到。
此时你需要注意的是 0x100530000 是你的基址，
```
```
程序提示`请输入基值`时输入0x100530000
程序提示`请输入调用栈地址`时输入0x100537b28或0x100537a60
这时候就会解析出奔溃的方法
```
