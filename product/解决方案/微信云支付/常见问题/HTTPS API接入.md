### 请求HTTPS API是否限定特定的语言？
参考 接口调用说明 按照文档的请求格式发送https请求即可，对于实现语言没有特定的要求。

### 请求返回参数authen_code错误

返回例如：
"response_content":"{"status":101,"description":"参数authen_code错误.","log_id":1912969760,"internal_status":7}"}

解决方法：
参考以下文档进行重新计算后再尝试请求
https://cloud.tencent.com/document/product/569/37627
