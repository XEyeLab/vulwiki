# Error Info

## 0x01 漏洞描述

应用程序未对代码逻辑进行异常捕获，攻击者可通过输入异常字符串、异常类型、异常长度、畸形参数、增加删除参数、修改请求方法、异常请求头等途径是程序异常，从而导致应用程序抛出异常错误信息。

## 0x02 漏洞危害

攻击者通过构造特殊的攻击向量使应用程序抛出异常，可能导致应用绝对路径泄漏，源代码泄漏，敏感函数、控制器等泄漏，SQL语句泄漏，数据库敏感信息泄漏，接口信息等敏感信息泄漏。

攻击者可以利用这些信息实施进一步的攻击。

## 0x03 修复建议

1. 线上应用务必关闭debug模式。
2. 代码逻辑中尽量保证存在异常处理逻辑。
3. 错误信息统一处理，比如统一跳转首页、显示404页面、500页面等。
4. 严格校验用户输入数据，细化服务端处理颗粒度。
5. 不要相信逻辑上的跳转语句。
6. 确保异常之后的代码不会运行。
