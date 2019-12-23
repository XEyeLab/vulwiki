## 文件包含漏洞

#### 漏洞描述：

##### 文件包含漏洞多数情况出现在PHP中，当然jsp中也存在，文件包含分为本地包含与远程包含。

#### 漏洞危害：

1.绕过WAF上传木马文件

2.加载有害的远程内容，影响程序运行。

#### 漏洞修复：

1.关闭allow_url_fopen

2.避免使用include参数

3.使用web检测文件内容