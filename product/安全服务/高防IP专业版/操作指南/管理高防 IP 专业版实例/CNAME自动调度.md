高防 IP 专业版的 CNAME 自动调度功能默认开启。当攻击流量超过当前 IP 组的防护峰值，导致当前 IP 组的高防 IP 被封堵时，高防 IP 专业版将按照策略，通过 CNAME 自动将该高防 IP 的流量调度到下一个 IP 组。
高防 IP 专业版实例创建时，将根据购买时选择的保底防护峰值和弹性防护峰值分配1 - 5个高防 IP，并分为1 - 3个 IP 组（其中第1组为初始区域的 IP 组），不同 IP 组的防护能力大小不同。分配 IP 情况具体如下：
- **广州、北京地区：**当选择的最高 [防护峰值](https://cloud.tencent.com/document/product/1005/36640#.E9.98.B2.E6.8A.A4.E5.B3.B0.E5.80.BC) ≤ 100Gbps时，分配1个广州（或北京） BGP 高防 IP，为第1组 IP。当100Gbps < 最高防护峰值 ≤ 300Gbps时，再分配1个上海 BGP 高防 IP，为第2组高防 IP。当最高防护峰值 > 300Gbps时，则再分配3个高防 IP，分别是南京电信高防 IP、南京联通高防 IP和上海 BGP 高防 IP，为第3组 IP。
- **上海地区：**当选择的最高防护峰值 ≤ 300Gbps时，分配1个上海 BGP 高防 IP，为第1组 IP。当最高防护峰值 > 300Gbps时，则再发放3个高防 IP，分别是南京电信高防 IP、南京联通高防 IP和上海 BGP 高防 IP，为第2组高防 IP。

### 示例
如果用户在广州区域购买了一个高防 IP 专业版实例，规格是“20Gbps 保底防护峰值 + 400Gbps 弹性防护峰值”，此时最高防护峰值为400Gbps，当超过300Gbps，分配3组 IP，分别是：1个广州 BGP 高防 IP，上海 BGP 高防 IP，南京电信高防 IP、南京联通高防 IP 和上海 BGP 高防 IP。
在 [开启自动回切](https://cloud.tencent.com/document/product/1005/30858#.E8.87.AA.E5.8A.A8.E5.9B.9E.E5.88.87) 时：
1. 非攻击或小流量攻击状态下，使用第1组 IP 提供服务。
2. 当出现攻击且攻击流量超过20Gbps时，广州 BGP 高防 IP 遭遇封堵，切换到第2组 IP 进行防护。
3. 当攻击流量超过300Gbps时，导致上海 BGP 高防 IP 进入封堵，此时切换到第3组 IP 进行抵御，访问流量将按负载均衡方式进行分发处理。
4. 当第3组 IP 全部被封堵，且当前第1组 IP 已到解封时间被解除封堵，则自动回切到第1组 IP 进行防护，以此循环。
5. 直到所有 IP 组都被封堵，且都未到解封时间或自助解封次数已耗尽时，用户的业务访问才会中断。

另外，若未开启自动回切，则在情况4时，当第3组 IP 全部被封堵，无论当前第1组高防 IP 是否解封，都不会自动调度至第1组 IP，用户只能通过自助解封操作来恢复业务。当自助解封次数全部用完，则业务访问将出现中断。
