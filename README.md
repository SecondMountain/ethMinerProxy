# ethMinerProxy
eth 中转服务器

提供功能：   
1、总算力曲线     

2、aes加密，数据不泄露，将数据加密端放在局域网内让矿机链接避免了挖矿特征泄露的问题 
 
3、机器掉线邮件提醒（掉线以后5分钟内发送邮件）

server.exe 为中转服务器，抽水0.5%，量大的用户找我修改更小的抽水    
clinetserver.exe为加密本地服务器    
    
使用方式（目前只支持windows端，linux端打包测试中）    
下载到本地双击即可运行（配置文件需要和exe文件同目录）

配置文件介绍如下：   
server端（中转服务器）
```
  "self-port": 25555, #程序监听的服务端口
  "is-ssl": true,       #矿池链接是否使用ssl，建议使用ssl的连接
  "pool-port": 5555,    #矿池端口
  "pool-ip": "asia2.ethermine.org", #矿池ip
  "web-port": 25556,    #本地开启的web服务端口，开启服务后可访问 http://ip:25556查看中转服务器信息
  "pump-per": 1,    #抽水比例，1为1%，2为2%，以此类推
  "pump-ssl":true,  # 抽水矿池链接是否为ssl加密链接
  "pump-port": 5555, #抽水矿池端口
  "pump-ip": "asia2.ethermine.org", #抽水矿池链接
  "pump-wallet": "0x916A852E18962E0D4d84a4d1a380DE810dF0ab07", #抽水钱包地址
  "pump-name": "fee", #抽水旷工名
  "max-num": 500, # tcp最大链接数
  "encrypt": "aes", # 本地服务和client的数据链接加密方式，不要修改
  "salt": "MIICYAIBAAKBgQCVKUIKxkl0hgRWS3+Z",  #数据加密盐值server和clientserver的配置要一致，长度为32位
  "nonce": "minerhappy"  #数据加密盐值server和clientserver的配置要一致，长度随意

```

本地加密端
```
{
  "self-port": 3333,  # 本地服务端口， 矿机链接的时候使用stratum+tcp//本机ip：3333
  "encrypt": "aes", #本地服务和client的数据链接加密方式，不要修改
  "max-num":50,  #tcp最大链接数
  "server-port": 25555, # server端（中转服务器）端口
  "server-ip": "192.168.1.5", #server端（中转服务器）ip
  "salt": "MIICYAIBAAKBgQCVKUIKxkl0hgRWS3+Z",  #数据加密盐值server和clientserver的配置要一致，长度为32位
  "nonce": "minerhappy"  #数据加密盐值server和clientserver的配置要一致，长度随意
}
```
如有使用问题可给作者留言：QQ：995339760
