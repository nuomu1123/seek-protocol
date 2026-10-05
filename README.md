# Seek Protocol · 三层提纯协议

> 你才是决定者，AI 做的是帮你看清楚。
> You are the decision-maker. AI's job is to help you see clearly.

一个零依赖的单文件交互式决策助手。通过 **AI 主动提问 → 注意力分配 → 插件化分析 → 对抗验证** 四层流程，帮你看清复杂问题、看清分歧、看清自己该判断什么——最终决策权永远在你手中。

A zero-dependency, single-file interactive decision assistant. It runs a strict four-layer protocol — proactive questioning, attention allocation, pluggable mental models, and adversarial validation — to help you see the problem, the trade-offs, and what only you can judge.

## 快速开始

无需安装、无需联网、无需构建——用浏览器打开 `index.html` 即可。

```bash
git clone https://github.com/nuomu1123/seek-protocol.git
cd seek-protocol
# 双击 index.html，或：
open index.html        # macOS
start index.html       # Windows
```

## 截图

| L0 · AI 主动提问 | L3 · 对抗验证与分歧地图 |
|---|---|
| ![L0 信息收集](docs/screenshot-l0.png) | ![L3 验证与反馈](docs/screenshot-l3.png) |

## 四层流程

| 层 | 名称 | 做什么 |
|---|------|--------|
| L0 | 信息收集 | AI 主动提出最多 3 个带 A/B/C 选项的问题；可「跳过」，用默认假设推进并标注「基于假设」 |
| L1 | 注意力分配 | 划定边界（时间 / 资源 / 底线）→ 定位核心矛盾（X vs Y）→ 列出最多 3 个次要矛盾 → 建议一个方向深入 |
| L2 | 解释与解决 | 从模型库自动匹配一个思维模型并说明理由，从时间 / 利益相关方两个角度分析，给出初步结论 |
| L3 | 验证与反馈 | 构建最强反方立场（不是稻草人），呈现分歧地图（事实 / 价值 / 不确定性），最后由你裁决 |

## 指令

| 指令 | 作用 |
|------|------|
| `继续` | 进入下一层 |
| `重选` | 返回上一层重新计算 |
| `跳过` | L0 阶段跳过提问，用默认假设推进 |
| `暂停` | 保存进度（刷新或重开自动恢复） |
| `重置` | 归档当前会话，开始新问题 |
| `直接给结论` | 跳过对抗验证给出结论（标注「未经对抗验证」） |

L0 快速作答格式：`1A 2B 3C`，也支持自然语言补充。

## 思维模型库

内置 5 个模型，由 AI 按问题特征自动匹配：

| 模型 | 适用场景 | 关键问题 |
|-----|---------|---------|
| 经济学-机会成本 | 资源有限、需要取舍 | 这个选择放弃了什么？ |
| 心理学-确认偏误 | 已有倾向、需要检验 | 我在寻找支持还是真相？ |
| 物理学-熵 | 混乱无序、需要整理 | 系统的无序度在增加吗？ |
| 生物学-生态位 | 竞争定位、差异化 | 我在哪个位置有优势？ |
| 数学-约束优化 | 多变量、找最优解 | 约束条件下什么是可行的？ |

在「模型库」面板中添加自定义模型，格式：`模型名称 | 适用场景 | 关键问题`。自定义模型与内置模型同等参与自动匹配。

## 特性

- **不适用场景直通**：简单事实查询、紧急情况、纯创意请求自动识别，不强行走四层
- **可编辑输入**：悬停自己发过的消息，点「编辑」回滚到该节点重新计算
- **历史记录**：完成的会话自动存档（localStorage），可导出 JSON
- **进度指示**：顶部 LED 灯实时显示当前层级
- **单 AI 模式声明**：L3 反方由同一 AI 扮演，输出中明确建议用另一个 AI 交叉验证
- **隐私**：所有数据仅保存在浏览器本地，不发送任何网络请求

## 技术

纯 HTML + CSS + 原生 JavaScript，状态机驱动，无任何外部依赖。当前版本的分析引擎为内置启发式规则（离线可用）；接入真实 LLM API 的扩展点预留在各层生成函数中（`runL1` / `runL2` / `runL3`）。

## License

[MIT](LICENSE)
