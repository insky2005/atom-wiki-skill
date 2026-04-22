# 编码器-解码器结构（Encoder-Decoder Structure）

## 内容

原始 Transformer 采用编码器-解码器结构：

**编码器：**
- 由 6 层相同的层堆叠而成
- 每层包含多头自注意力子层和前馈网络子层
- 均使用残差连接和层归一化

**解码器：**
- 同样 6 层
- 在编码器-解码器注意力层中，查询来自前一解码器层，键和值来自编码器输出
- 使用掩码自注意力以防止关注未来位置

## 来源

- transformer-overview.md

## 标签

#encoder-decoder #transformer #architecture #sequence-modeling

## 交叉引用

- [[transformer-self-attention]] - 编码器和解码器中的自注意力
- [[transformer-multi-head-attention]] - 多头注意力在编码器-解码器连接中的作用
- [[transformer-key-impact]] - BERT（仅编码器）、GPT（仅解码器）、T5（编码器-解码器）的变体
