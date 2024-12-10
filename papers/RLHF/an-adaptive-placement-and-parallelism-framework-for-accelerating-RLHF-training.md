市面上的 trlX、trl、deepspeed-chat 等都是很直接的模型放置策略：平铺策略。把所有的模型当作单个的实体，然后使用标准的切分方法。所以有一些限制，带来优化空间：
1.需要的显存大，通信开销也大（Zero3、DS）
2.不同的模型大小需要细粒度的模型放置策略
3.训练和推理负载完全不同，需要不同策略

训练：os、gradient和参数都需要 ZeRO

推理：只需要参数的分片(TP)

