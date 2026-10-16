# 贡献指南

感谢你愿意为 Actus 贡献代码。请先阅读本指南，并遵循 **一 PR 一事** 的原则。

## 基本原则

1. **一 PR 一事**：每个 Pull Request 只解决一个问题或实现一个功能。混杂多个目的的 PR 会被要求拆分。
2. **先搜开源，有→写动作，无→才进 builtin**：发现缺少的能力，先检查是否有现成的 CLI/MCP/HTTP 工具可包装为动作；确实没有才考虑 builtin 实现。
3. **写清范围与出口条件**：PR 描述必须说明改动文件范围、影响面，以及"出口条件"（合并前必须满足的验收标准）。

## 提交规范

- commit message 使用中文，格式：`类型: 摘要`（如 `feat: 新增 xxx 动作`、`fix: 修复 xxx`、`init: 初始化 xxx`、`docs: 更新 xxx`）。
- 一个 commit 只做一件事，保持提交原子性。

## 贡献流程

```bash
# 1. Fork 本仓库并克隆
git clone https://github.com/Actus-Actions/actus.git
cd actus

# 2. 创建功能分支
git checkout -b feat/my-new-action

# 3. 在 actions/<目录>/ 下新建动作（.actus.md）
#    <目录> 按分类选择：ecosystem / cli / http / demo / system / text / automation

# 4. 本地校验（必须通过）
python -m actus validate

# 5. 提交并推送
git commit -m "feat: 新增 xxx 动作"
git push origin feat/my-new-action

# 6. 提交 PR（一 PR 一事，写清范围 + 出口条件）
```

## PR 出口条件

- [ ] 改动文件范围已在 PR 描述中列明
- [ ] 新增/修改的动作通过 `actus validate`（errors=0）
- [ ] 涉及 schema/契约变更时，`contracts/` 同步更新
- [ ] 涉及引擎改动时，附上 `python -m actus doctor` 与相关测试结果
- [ ] CI 必须绿（若配置了 CI）

## 代码风格

- 动作使用 `.actus.md`（Markdown 即代码），遵循 `docs/` 中的动作规范。
- 引擎代码遵循 Python 官方风格（PEP 8），类型标注完整。

## 行为准则

- 尊重他人，礼貌沟通；技术讨论对事不对人。
- 不提交与 PR 目标无关的改动。
- 涉及安全、凭据、审计日志相关改动，请在 PR 中主动说明影响面。
