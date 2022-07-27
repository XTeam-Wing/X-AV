# X-AV
X系列安全工具-AV免杀框架-BypassAV

源码在知识星球RedTeaming

Web版

![](https://redteamwing.oss-cn-hongkong.aliyuncs.com/20210518145602.png)

## 加载方式
- Syscall
- Uuid
- CreateFiber
- CreateProcessWithPipe
- EtwpCreateEtwThread
- 等

## 加密方式
- XOR
- RC4
- AES256

## 沙盒检测,动态防御

## 符号表混淆,静态分析防御


## 权限维持
权限维持功能目前还没有加入
## 生成伪造证书
有点多余,可选项。
## 使用方法

```
❯ ./X-AV -h

 ____  _          _ _  ____          _     _____           _
/ ___|| |__   ___| | |/ ___|___   __| | __|_   _|__   ___ | |___
\___ \| '_ \ / _ \ | | |   / _ \ / _` |/ _ \| |/ _ \ / _ \| / __|
___) | | | |  __/ | | |__| (_) | (_| |  __/| | (_) | (_) | \__ \
|____/|_| |_|\___|_|_|\____\___/ \__,_|\___||_|\___/ \___/|_|___/

Version 1.0-RedTeamWing
						Loader Method:
						CreateFiber
						Syscall
						CreateProcess
						CreateProcessWithPipe
						CreateRemoteTread
						CreateRemoteTreadNative
						CreateThread
						CreateThreadNative
						UUIDFromString
						RtlCreateUserThread
						EtwpCreateEtwThread

						Encryption Method:
						Xor
						AES256
						RC4

Usage of ./X-AV:
  -domain string
    	fake domain
  -encrypt string
    	chose encryption (default "hex")
  -key string
    	encryption key (default "1314")
  -loadermethod string
    	选择shellcode加载方式 (default "CREATEFIBER")
  -o string
    	output path (default "boomsec.exe")
  -password string
    	fake domain cert password (default "201314")
  -persistence
    	Persistence[True or False]
  -salt string
    	aes 加密的salt
  -sandbox
    	Bypass Sandbox Check (default true)
  -shellcodepath string
    	shellcode path (default "shellcode.bin")
  -v	display detail infomation
  ```
  
 ### XOR加密
  每种加密都支持前面五种加载方法
```
./X-AV -shellcodepath cdn.bin -o xor.exe -key wing -encrypt xor  -loadermethod uuid
```
![](https://i.loli.net/2021/05/14/2HfmgtLoRdKiWkG.png)
 ### AES加密
 aes需要加salt
```
./X-AV -shellcodepath cdn.bin -o aes.exe -key wing -encrypt aes  -loadermethod uuid -salt wing
```
### RC4
```
./X-AV -shellcodepath cdn.bin -o rc4.exe -key wing -encrypt rc4  -loadermethod uuid
```

## 测试结果
对象：WindowsDefender
基本测试这个AV就行了
![](https://i.loli.net/2021/05/14/Q8RvafxMIFKGXWU.png)

![image](https://user-images.githubusercontent.com/25416365/118236750-0ded1700-b4c9-11eb-8e63-1b92b6f668b5.png)


