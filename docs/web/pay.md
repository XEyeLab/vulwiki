# Defective Payment

## 0x01 漏洞描述

支付漏洞是指应用程序在支付环节，由于数据包中没有签名校验或者签名算法太容易而被破解，导致可以直接拦截数据包，修改支付订单中的参数为恶意非法参数而导致的支付缺陷。

## 0x02 常见应用场景

### 2.1 购买

- 修改支付的价格
- 修改支付的状态
- 修改支付的数量or价格为999999999999...
- 修改购买数量or价格为负数
- 修改金额为负数
- 重放成功的请求（包含支付附加值时等）
- 使用任意用户优惠券
- 修改运费价格
- 修改支付接口为不存在的支付接口
- 替换支付订单号
- 并发数据库锁处理不当

### 2.2 业务风控

- 刷优惠券
- 无限试用
- 套现

### 2.3 订单

[同越权漏洞](../yuequan/)

## 0x03 漏洞危害

攻击者利用支付缺陷，通过绕过签名、修改支付参数等各种途径，直接会给企业造成巨大风险。

## 0x04 修复建议

1. 对支付数据表进行数据包加密；
2. 对提交数据包做数据签名处理，保证支付数据参数无法修改；
3. 服务端效验客户端提交的参数；
4. 服务端严格校验支付参数的合法性，比如金额、数量的长度，金额、数量的正负等；
5. 对于用户提交的数据，应从数据库重新拉取，并校验用户提交与用户所有是否匹配；
6. 对于多线程等并发问题，可以先打入队列，在与数据库交互；