
### Wireshark 简介

[官方下载地址](https://www.wireshark.org/download.html)

启动后,通常需要选择一个接口, 双击进入抓包界面.
Ethernet:en0(以太网卡)和Wi-Fi:en1(无线网卡)是常用的两个接口.

#### 创建虚拟网卡

##### 1. 获取iPhone的UDID
插入手机, 输入以下命令,然后获取iPhone的UDID:

```
$ system_profiler SPUSBDataType | grep "Serial Number:.*" | sed s#".*Serial Number: "##
```

##### 2. 为iPhone创建虚拟网卡

```
$ rvictl -s decb66caf7012a7799c2c3edxxxxxxxx7f5a715e
```

> 可以使用rvictl -x [UDID]命令在需要的时候去除网卡。

##### 3. 再次查看已有接口
```
$ ifconfig -l
```


#### 启动虚拟网卡

打开, 本地接口选择`rvi0`


### 常用过滤规则


```
http.host==magentonotes.com
http.host contains magentonotes.com
//过滤经过指定域名的http数据包，这里的host值不一定是请求中的域名

http.response.code==302
//过滤http响应状态码为302的数据包

http.response==1
//过滤所有的http响应包

http.request==1
//过滤所有的http请求，貌似也可以使用http.request

http.request.method==POST
//wireshark过滤所有请求方式为POST的http请求包，注意POST为大写

http.cookie contains guid
//过滤含有指定cookie的http数据包

http.request.uri==”/online/setpoint”
//过滤请求的uri，取值是域名后的部分

http.request.full_uri==” http://task.browser.360.cn/online/setpoint”
//过滤含域名的整个url则需要使用http.request.full_uri

http.server contains “nginx”
//过滤http头中server字段含有nginx字符的数据包

http.content_type == “text/html”
//过滤content_type是text/html的http响应、post包，即根据文件类型过滤http数据包

http.content_encoding == “gzip”
//过滤content_encoding是gzip的http包

http.transfer_encoding == “chunked”
//根据transfer_encoding过滤

http.content_length == 279
http.content_length_header == “279″
//根据content_length的数值过滤

http.server
//过滤所有含有http头中含有server字段的数据包

http.request.version == “HTTP/1.1″
//过滤HTTP/1.1版本的http包，包括请求和响应

http.response.phrase == “OK”
//过滤http响应中的phrase

```

### 自用过滤规则


```
http.host contains 10.8.207.84 &&  http.request.uri contains "getMeetingList"

// 过滤ip 和 uri

```
