**漏洞成因**

没进行权限校验。

## 影响范围

Nacos-Sync 3.0

## 发现方式

### 一、fofa发现

```
title="nacos" &amp;&amp; title=="Nacos-Sync"
```

![image-20230810092327977](./Nacos-Sync.assets/image-20230810092327977.png)

### 二、路径拼接

```
/#/serviceSync
```

## 利用方式

访问之后直接是进入后台的样子~

![image-20230810092337651](./Nacos-Sync.assets/image-20230810092337651.png)