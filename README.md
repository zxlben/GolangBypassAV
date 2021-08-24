# GolangBypassAV
研究利用golang来bypassAV

## 前言
免杀这块本来就不是web狗擅长的，而且作为一个web狗也没必要花太多时间来折腾这个，达到能用就行，不要追求全部免杀，能免杀目标就行。


## 免杀思路
### 静态
静态免杀比较简单，可选加密payload或者分离payload。  
核心：   
把特征去除即可过静态，某些杀毒软件带沙箱，还需要考虑反沙箱。   
除此之外还可以考虑如下方式：     
由于要引入net包，导致文件大小比较大。我不做测试了。    
把payload分离远程服务器   
把payload隐写到图片     
总之就是各种分离  

### 动态
golang和c++有点不一样不需要考虑处理IAT。    
敏感api越少越好比如注册表操作、添加启动项、添加服务、添加用户、注入、劫持、创建进程、加载DLL等等    
核心：   
想法设法的把shellcode加载到内存里面。    
使用内核层面Zw系列的API，绕过杀软对应用层的hook监控。  
敏感操作可以分步进行，如申请内存先申请读写，再改成可以执行。不要一来就直接申请读写执行的内存。  





## 说明

2021.8.24  
直接用gen里面代码进行生成,演示视频已经放公众号，目前免杀已达目的更新会放缓。   
注意：建议每次使用之前手动改一下key,如果被杀改一下关键字即可。    







## 编译命令

```bash

go build -ldflags="-s -w" -o main1.exe -race main.go

go build -ldflags="-s -w" -o main1.exe

go build -ldflags="-s -w -H=windowsgui" -o main2.exe

set GOOS=windows GOARCH=amd64;go build -o main.exe


```



## 参考
https://github.com/Ne0nd0g/go-shellcode   
https://github.com/Rvn0xsy/BadCode    
https://github.com/Airboi/bypass-av-note  
https://github.com/brimstone/go-shellcode          
https://github.com/timwhitez/Doge-Loader          
https://github.com/fcre1938/goShellCodeByPassVT          