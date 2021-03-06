## 概述
规则引擎支持用户配置规则将符合条件的设备上报数据转发到 [消息队列 CKAFKA](https://cloud.tencent.com/product/CKafka) （以下简称 CKAFKA ），用户的应用服务器再从 CKAFKA 中读取数据内容进行处理。以此利用 CKAFKA 高吞吐量的优势，为用户打造高可用性的消息链路。  

下图展示了规则引擎将数据转发给 CKAFKA 的整个过程：
![avatar](https://main.qcloudimg.com/raw/ae9179db06123982f14857891aeabb8a.png)

## 配置
1. 登录 [物联网通信控制台](https://console.cloud.tencent.com/iotcloud)，单击左侧菜单【规则引擎】。
2. 进入规则引擎页面，单击需要配置的规则。
3. 在规则详情页面，单击【添加行为】。
4. 在弹出的“新增行为”窗口，选择行为“数据转发到消息队列（CKAFKA）”；依次选择 CKAFKA 实例和 Topic，单击【创建】即可。
![avatar](https://main.qcloudimg.com/raw/29a2d077cb2a40fb8db6d6e884d53219.png) 
>?第一次使用时会提示用户授权访问 CKAFKA，用户需单击【授权访问 CKAFKA】才能继续创建。
![](https://main.qcloudimg.com/raw/4a6bd8af7de3fe642ef2f47c41626cac.png)
5. 完成以上配置后，物联网通信平台会将符合规则条件的设备上报数据转发至用户配置的 CKAFKA 。您可以参考 [创建实例和 Topic](https://cloud.tencent.com/document/product/597/30931) 文档，在应用服务器上读取数据并进行处理。


