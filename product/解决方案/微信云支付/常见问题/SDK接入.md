## 对回包status的理解

问题：调用退款接口返回的rsp里的status是0，表示成功，为什么点开原支付公众号里查询这个退款单状态是退款失败？

回答：判断status和internal_status只说明请求没有问题，不代表退款成功 

## 刷卡支付接口

问题：刷卡支付接口的OrderClient里的machine_no哪里获取的
回答：机器的唯一标识id，如windows电脑就是mac地址， 对接方可以使用对应系统的api接口获取， 如是windows平台，使用windows api去获取机器mac地址； 这个字段云支付不强制校验内容但一定要填。
