# The-PaddlePaddle-implementation-MobileFormer
Using PaddlePaddleto reproduce the MobileForMer model, and complete the quantity of the parameters close to it.

- <a href="https://arxiv.org/abs/2108.05895" target="_blank">`Go to Read Paper`</a>
- `done date`: `2021-11-13`
- 模型结构(组网)类型:

    - `DepthWiseConv`: 深度卷积--每个通道分配单个卷积核并输出，in_channels=out_channels
    - `PointWiseConv`: 逐点卷积--1x1卷积
    - `MLP`: 多层感知机
    - `DyReLU`: 动态ReLU
    - `Mobile`: MF中的Mobile卷积部分
    - `Attention`: 简单的普通注意力机制
    - `DropPath`: Path丢弃
    - `Former`: MF中的Former纯注意力部分
    - `ToFormer_Bridge`: 从Mobile到Former的桥
    - `ToMobile_Bridge`: 从Mobile到Former的桥
    - `Stem`: 渐入层
    - `BottleNeck`: BottleNeck -- 支持Lite类型
    - `Classifier_Head`: 分类头
    - `MFBlock`: MobileFormer最小实现单元
    - `MobileFormer`: 网络实现

- 构建模型接口说明:

    - `MobileFormer`: 构建MobileFormer模型的基类
        - 传入`model_type`: [`26m`, `52m`, `96m`, `151m`, `214m`, `294m`, `508m`],
        - 生成对应的模型
    - `check_model_size`: 检查模型参数量对比情况(与原论文)

- 参数对齐情况说明:
  -
  ```python
    """Model Compare
        Name    Params   Review_Size    Save_Model_Size(.pdparams)
        508M:   14.0M       13.982M          54.724M
        294M:   11.4M       11.390M          44.601M
        214M:   9.4M        9.411M           36.843M
        151M:   7.6M        7.612M           29.814M
        96M:    4.6M        4.602M           18.036M
        52M:    3.5M        3.502M           13.737M
        26M:    3.2M        3.207M           12.586M
    """
  ```
- 支持的论文模型:
  - 26m  —— MobileFormer(model_type = '26m')
  - 52m  —— MobileFormer(model_type = '52m')
  - 96m  —— MobileFormer(model_type = '96m')
  - 151m —— MobileFormer(model_type = '151m')
  - 214m —— MobileFormer(model_type = '214m')
  - 294m —— MobileFormer(model_type = '294m')
  - 508m —— MobileFormer(model_type = '508m')
