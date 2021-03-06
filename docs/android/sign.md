# 安装包签名

## 0x01 漏洞描述

Android系统要求安装的应用必须用数字证书进行签名后才能安装，并且签名证书的私钥由应用开发者保存。签名证书的生成也由开发者自己生成。在应用安装时会校验包名（package name）和签名，如果系统中已经存在了一个相同的包名和签名的应用，将会用新安装的应用替换旧的；如果包名相同但是签名不同，则会安装失败。

应用签名完后在应用的META-INF目录下会有三个文件： CERT.RSA、CERT.SF和MANIFEST.MF。

    MANIFEST.MF中保存了所有其他文件的SHA1摘要并base64编码后的值。
    
    CERT.SF文件是对MANIFEST.MF文件中的每项中的每行加上“\r\n”后，再次SHA1摘要并base64编码后的值（这是为了防止通过篡改文件和其在MANIFEST.MF中对应的SHA1摘要值来篡改APK，要对MANIFEST的内容再进行一次数字摘要）。
    
    CERT.RSA文件：包含了签名证书的公钥信息和发布机构信息。
## 0x02 漏洞危害

签名信息中包含的组织信息，将便于用户识别安装包的真伪。

## 0x03 修复意见

* 在应用程序发布时使用企业签名对安装包进行签名。