# 免费申请IBM 无使用期限VPS 无需信用卡一个邮箱就可以申请

自从谷歌2020年8月份开始从原来365天的免费试用的正常变更为90天的试用后，看看是否有其他更好的替代薅羊毛方案！

完成第一部分 就可以使用了，如果进阶可以继续完成第二 第三部分
让我们开始吧！

### 1. 我们利用开源免费的Cloud Foundry项目来搭建V2ray

##### 1.1. 申请IBM免费VPS
> 地址：https://cloud.ibm.com/


 //老的安装代码
 
 wget --no-check-certificate -O install.sh https://raw.githubusercontent.com/Ericssuny/IBMYes/master/install.sh && chmod +x install.sh && ./install.sh
 
 //cli错误安装下面第一个代码
 
 ibmcloud login -a 'https://cloud.ibm.com' -r 'us-south'
 
 （备用）ibmcloud target --cf-api 'https://api.us-south.cf.cloud.ibm.com'

# 1.2. V2ray一键安装代码(9月12日 00:01 更新)

```
wget --no-check-certificate -O install.sh https://raw.githubusercontent.com/bigfangfang/IBMVPS/master/install.sh && chmod +x install.sh  && ./install.sh

```

> 注意事项：
>> 1. 记住填写的 应用名称 建议写：bigfang 
>> 2. 内存大小选择256m
>> 3. 一键安装完成后 保存生成VMESS链接

##### 1.3. 客户端配置

导入vmess链接

### 2. 利用Github创建每周开关机一次任务


##### 2.2. 建立4项secret

> IBM_ACCOUNT // IBM Cloud的登录邮箱和密码
```
your@email.com  
password
```
> IBM_APP_NAME // 应用的名称
```
bigfang
```

> REGION_NUM // 区域编码
```
7
```

> RESOURSE_ID // 资源组ID
```
你的ID
```

>> 如何查找RESOURSE_ID？
>>> *打开IBM cloud shell，输入下面代码*

```
ibmcloud resource groups
```
 >>> *显示出来的ID就是你的RESOURSE_ID*
 
 
##### 2.3. 运行IBM项目

###### 2.3.1. 点击Actions，再点击绿色的框  
###### 2.3.2. 再点击Code--github/workflows---ibm.yml--右边的编辑按钮 修改一下第37行  
修改完点击start commit。
再回到Actions就能看到正在运行的项目，等到变成绿色的对号就运行了

### 3. cloudflare加速

登陆Cloudflare官网点击workers--创建--复制脚本--修改对应域名

```
addEventListener(
"fetch",event => {
let url=new URL(event.request.url);
url.hostname="bigfang.us-south.cf.appdomain.cloud";
let request=new Request(url,event.request);
event. respondWith(
fetch(request)
)
}
)
```

点击“发送”出现404也没有问题 直接保存部署
这时候会给一个网址，..workers.dev域名,这是cloudflare中转的域名

### 4. 客户端配置


### 5. 找回Vmess链接  


wget --no-check-certificate -O vmess.sh https://raw.githubusercontent.com/bigfangfang/IBMVPS/master/vmess.sh && chmod +x vmess.sh  && ./vmess.sh


=============================================================  
=============================================================  
请注意如果出现2个或者3个红色的FAILED就说明你的VMESS连接是无法连接外网的。这个时候需要去排查问题，可以通过这个影片去仔细看看可能能找到答案 https://bit.ly/2ZjVCkN  
或者观看YouTube影片 IBM Cloud VPS 详细分享：https://www.vbaond.com
如果你看到只有一个红色的Failed 那么恭喜你大概率你的Vmess连接有效！Vmess导入客户端后，请务必将域名中bigfang更改为你的应用程序名称！请务必根据在cloudflare中加速  

