TSBCV: 面向草原承包合同的空白一致性校验模块
TSBCV (Two-Stage Blank Consistency Verification) 是一个基于两阶段语义建模的智能校验模块，专门用于解决模板填空式合同（如草原承包合同）中复杂的空白项逻辑冲突问题。

📌 核心痛点：为什么“字符串匹配”不够用？
在传统的合同审查中，空白项一致性校验面临以下挑战：

语义漂移：相同含义的字段分散在不同条款中，表述方式不完全一致。

语境依赖：必须结合局部上下文（如前后的动词、量词）才能判断空白项的真实语义角色。

逻辑耦合：系统不仅要识别“填了什么”，还要判断“该位置本应填什么”以及它与全文其他位置的对应关系。

典型错误示例：

<p align="center">
  <img width="596" height="344" alt="image" src="https://github.com/user-attachments/assets/74b735a6-2e67-4974-8c6c-57bea15fa469" />
</p>

🔴 冲突填写：不同语义的空白项填写了相同内容。

🔵 不一致填写：相同语义的空白项填写了不同内容。

🏗️ 模块架构 (Architecture)
TSBCV 通过三个核心单元的协同作用，同时利用局部语义线索与文档级结构信息。

<p align="center">
  <img width="906" height="423" alt="image" src="https://github.com/user-attachments/assets/196e77e5-7040-4469-ba41-a3c71c2cc845" />
</p>

1. 空白语义表示单元 (Semantic Representation)
负责对合同文本中的空白字段及其上下文进行统一编码，生成高维度的初始字段表示。

2. 局部上下文感知单元 (Local Context Awareness)
功能：提取空白项附近的关键词和约束描述。

目的：使模型能够准确识别当前空白项在特定位置承担的语义角色。

3. 全局关系更新与一致性判定单元 (Global Consistency)
功能：在全文范围内建模不同空白字段之间的“对应”与“区别”关系。

结果：输出最终的一致性判定结果，识别潜在的填写冲突与逻辑不一致。

🌟 主要特性 (Key Features)
✅ 双阶段建模：结合局部感知与全局关联，告别简单的规则匹配。

✅ 跨条款识别：能够自动建立跨句、跨段甚至跨条款的语义槽位对应关系。

✅ 高效审查：针对草原承包合同等长文本，显著降低人工逐项核对的漏检率。

✅ 结构一致性增强：提升合同文本的规范性和可执行性，降低后续履约的解释成本。

📊 案例演示 (Case Study)
以下展示了 TSBCV 在草原承包合同中的实际表现：它能够精准识别出分散在合同各处的字段是否指向同一实体，并标记出其中的逻辑矛盾。

<p align="center">
  <img width="875" height="806" alt="image" src="https://github.com/user-attachments/assets/22b7038e-bdbd-4602-be28-1b6bfe20a708" />
</p
