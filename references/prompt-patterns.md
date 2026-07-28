# 提示词模式

按需读取并裁剪；不要把所有区块机械拼接到每个请求。

## 通用生产任务

```text
<role>
你是负责完成[领域/职责]任务的助手。
</role>

<objective>
完成[具体结果]。
</objective>

<context>
[必要背景、输入数据和术语]
</context>

<constraints>
- 必须：[硬性要求]
- 不得：[禁止项]
- 范围：[任务边界]
</constraints>

<evidence_and_validation>
- 使用[来源或材料]支持结论。
- 检查[关键风险或正确性条件]。
</evidence_and_validation>

<success_criteria>
- [可观察的完成标准 1]
- [可观察的完成标准 2]
</success_criteria>

<output_format>
先给出[结论/交付物]，再给出[证据/限制/下一步]。
</output_format>
```

## 编码代理

```text
<objective>
在不改变范围外行为的前提下，实现[功能或修复]。
</objective>

<workflow>
- 先检查相关代码、配置和现有测试。
- 直接完成范围内的本地修改。
- 运行相关的非破坏性测试、类型检查或静态分析。
- 不要修改无关文件或顺带重构。
</workflow>

<approval_boundaries>
外部写入、破坏性操作、安装未授权依赖、产生费用或明显扩大范围前必须确认。
</approval_boundaries>

<success_criteria>
- [行为要求]
- [兼容性要求]
- [测试要求]
</success_criteria>

<output_format>
总结修改、列出验证结果，并报告仍存在的风险或未验证项。
</output_format>
```

## 只审查不修改

```text
审查[材料]以发现[风险类型]。检查相关上下文并报告结果，但不要实施修改。

对每个发现给出：位置、影响、发生条件、证据和具体修复建议。按严重程度排序。没有发现时明确说明检查范围和剩余风险。
```

## 短答案

```text
先给结论。保留支持结论所需的关键证据、重大限制和下一步。优先删去重复、冗长开场、泛泛安慰和非必要背景。
```

## API 设置起点

```json
{
  "model": "gpt-5.6-sol",
  "reasoning": {
    "effort": "medium"
  },
  "text": {
    "verbosity": "medium"
  }
}
```

仅把此设置作为评测起点。根据代表性任务的质量、延迟、令牌和成本结果调整。
