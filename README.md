# Aaron Zhang

**Building honest tools for quantitative research.**

Writing about AI-Native software engineering and quant tooling.
Blog: **[postcodeengineering.com](https://postcodeengineering.com)** · 300+ essays in Chinese.

---

## ⭐ vlab — 回测有效性检验工具

> 零依赖的资产配置回测实验室。诚实的回测，而不是漂亮的回撤曲线。
> Zero-dependency portfolio backtesting with an explicit validity layer.

**Most backtest tools help you produce numbers. vlab helps you prove the numbers aren't an artifact.**

| | |
|---|---|
| 🛡️ **Look-ahead guard** | 策略只能看到截至当天的数据。读 `mat[c][i+1]` 直接抛 `LookAheadError` —— 偷看未来从静默的作弊变成响亮的错误 |
| 📉 **Overfit gap** | 样本内选参数，样本外验成绩，同时算出「先知基线」。差距越大，「样本内挑出来的最好」就越可能只是运气 |
| 🔁 **Walk-forward** | 滚动前推重拟合，只用没见过的数据评判 |
| 🧪 **77 个回归测试** | 每个历史引擎缺陷都有测试钉死：休市日错位、权重静默归一化、现金按值传递 |
| 📦 **零第三方依赖** | 纯标准库。`git clone` 完就能跑，不需要 `pip install` 任何东西 |

```bash
git clone https://github.com/aazh2026/vlab && cd vlab
python3 -m unittest discover -s tests        # 77 tests, ~0.4s, no deps, no network
PYTHONPATH=src python3 -m vlab validate examples/momentum_rotation.py
```

**在线面板** → https://aazh2026.github.io/vlab/
**博客详解** → https://postcodeengineering.com/backtest-validity/

*所有结果均为基于历史数据的回测，不预示未来收益，不构成投资建议。*

---

### 我为什么做这个

我把自己的回测引擎重写了一遍，测试立刻抓到四个 bug —— 每一个都足以让结论反号。最讽刺的是现金策略报告 **23.65% 年化，而真实值是 1.8%**：`cash -= cost` 改的是局部副本，买入根本没扣钱。曲线很好看，数字是假的。

一个专门消灭「回测欺骗」的项目，自己留了后门，这跟它声称的原则直接矛盾。所以 vlab 从第一天起就把「读未来就报错」和「样本外检验」做成硬约束，而不是可选功能。

---

## 其他项目

| 项目 | 说明 |
|---|---|
| **[dsh-specgate](https://github.com/aazh2026/dsh-specgate)** | 需求覆盖率 —— 像测试覆盖率，但针对验收标准 |
| **[specgate](https://github.com/aazh2026/specgate)** | Requirement coverage for your codebase |
| **[flapjax-treasury-audit](https://github.com/aazh2026/flapjax-treasury-audit)** | FlapJax treasury 的链上独立审计 |
| **[taskmarket-mcp](https://github.com/aazh2026/taskmarket-mcp)** | Taskmarket 的只读 MCP server |
| **[csv-normalize](https://github.com/aazh2026/csv-normalize)** | 把任意 CSV 规范化成严格 schema |

---

## 写作

**[postcodeengineering.com](https://postcodeengineering.com)** —— AI-Native 软件工程与 Agent OS，300+ 篇中文长文。
RSS: https://postcodeengineering.com/feed.xml
