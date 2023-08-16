来源刨洞安全

SSTI

根据线索：

![图片](./Jeecg-Boot Freemarker 模版注入漏洞.assets/640.png)

直接用 `JADX` 找到对应代码

![image-20230816170240853](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170240853.png)

很直接嘛，直接传入 `sql`，那直接构造请求先试试：

![image-20230816170248064](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170248064.png)

居然还有黑名单

![image-20230816170255493](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170255493.png)

这里起码还有个 `SQL` 注入漏洞

线索中说明了用 `Freemarker` 处理了传入的 `sql` 语句，那直接打 `SSTI` 试试

![image-20230816170302778](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170302778.png)

![image-20230816170307411](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170307411.png)

JDBC RCE

漏洞利用有个前提，必须有 `H2` 驱动的依赖

用 `JADX` 在反编译的代码中搜索 `testConnection`，找到对应的接口

```
org.jeecg.modules.jmreport.desreport.a.a#a(org.jeecg.modules.jmreport.dyndb.vo.JmreportDynamicDataSourceVo)
```

![image-20230816170325141](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170325141.png)

在 `IDEA` 中查看

代码被压的爹妈都不认识了

![image-20230816170336818](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170336818.png)

![image-20230816170341778](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170341778.png)

根据入参 `@RequestBody JmreportDynamicDataSourceVo var1` 知道，传入一个 `JmreportDynamicDataSourceVo` 对象的 `JSON`

**JmreportDynamicDataSourceVo**

![image-20230816170351509](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170351509.png)

里面能自定义 `dbUrl`，那么就直接构造参数，试试看

`dbUrl` 用前段时间的 `metabase poc` 改改

![image-20230816170359088](./Jeecg-Boot Freemarker 模版注入漏洞.assets/image-20230816170359088.png)
