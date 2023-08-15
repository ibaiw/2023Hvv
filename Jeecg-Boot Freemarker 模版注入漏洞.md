漏洞危害

1、如果被攻击者利用，可直接getshell； 2、如果被攻击者利用，可被用于内网信息收集，扫描目标内网主机； 3、如果被攻击者利用，可攻击运行在内网或本地的应用程序； 4、如果被攻击者利用，可被用作攻击跳板；

修复方法

Jeecg官方暂未修复该漏洞，无法通过升级JeecgBoot版本修复该漏洞，建议： 1、临时禁用Freemarker高危的代码执行类，如：freemarker.template.utility.Execute（ftl利用方式较多，请自行判断）

```
POST /jeecg-boot/jmreport/qurestSql HTTP/1.1
Host: xxx.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2088.112 Safari/537.36
Accept-Encoding: gzip, deflate
Accept: /
Connection: close
Content-Type: application/json;charset=UTF-8
Content-Length: 129

{"apiSelectId":"1290104038414721025",
"id":"1"}
```

