# Actus — 拥抱生态的 AI 动作执行平台

![Actus](logo.svg)

> **一句话定位：拥抱生态，少造轮子。** 已有的能力（开源 CLI / MCP 生态 / Quicker / OpenKnowledge / 云 API）直接复用为动作，Actus 只专注三件事：**编排、治理、分发**。

Actus 是一套以 **Markdown 即代码** 为核心的 AI 动作执行平台。动作是结构化的 `.actus.md` 文档，由 AI 负责编写与执行，人类只需要用自然语言描述"想要什么"。

## 为什么选 Actus

| 维度 | Actus | GitHub Actions | n8n | Quicker |
|---|---|---|---|---|
| **定位** | 跨生态 AI 动作编排 | CI/CD 自动化 | 可视化工作流 | 鼠标快捷操作 |
| **动作形态** | `.actus.md`（数据，Git 友好分享） | YAML 工作流 | 节点连线 | 专有格式 |
| **生态观** | **任意第三方 = 一个动作**（不 fork 代码） | 自有 Actions 市场 | 自有节点库 | 自有动作集 |
| **治理模型** | trust 分级 + 审计日志 + 权限白名单 | 仓库权限 | 角色权限 | 无 |
| **AI 可生成** | 动作即 Markdown，AI 天然可读写 | 需理解 YAML schema | 需理解节点协议 | 需 GUI 操作 |
| **开源许可** | Apache-2.0（代码全开源，商业版为托管服务） | MIT | Apache-2.0（fair-code） | 闭源 |

## 核心理念：动作即数据

```
传统工具：代码 → 编译 → 二进制 → 安装 → 运行
Actus：   .actus.md（Markdown 文档） → 扫描 → 执行
```

- 动作是**数据不是代码**——`.md` 文档而非程序，Apache-2.0 不传染数据，动作可闭源商用
- **不 fork 第三方代码**——纯 API/CLI 调用封装，GPL 红线安全
- **Git 友好**——动作库可版本管理、可分享、可 PR 协作
- **AI 可读写**——LLM 天然理解 Markdown，生成动作无需专用 SDK

## 快速开始

环境要求：Python 3.10+，vools 基座 + vools.actus 引擎：`pip install "vools[actus]>=0.7.9"`

```bash
# 验证环境
python -c "import vools; print(vools.__version__)"
python -c "import vools.actus; print(vools.actus.__file__)"

# 安装与运行
cd engine
python -m actus scan          # 扫描动作，生成索引
python -m actus list          # 查看已注册动作
python -m actus run actus.hello --confirm   # 执行第一个动作
python -m actus doctor        # 诊断环境问题
python -m actus validate      # 校验所有动作
```

在 `actions/` 目录下新建 `.actus.md` 文件即可编写自己的动作（示例见 `docs/快速上手.md`）。

## CLI 命令一览

Actus CLI 提供 **100+** 子命令，覆盖动作全生命周期：

| 类别 | 命令 |
|---|---|
| 基础查询 | `actus list` / `actus info <id>` / `actus search <query>` / `actus scan` |
| 执行编排 | `actus run <id>` / `actus preview <id>` / `actus workflow <name>` / `actus exec <lang>` |
| 治理信任 | `actus validate` / `actus trust <id>` / `actus approve <id>` / `actus deps <id>` |
| 生态集成 | `actus mcp` / `actus dialog` / `actus triggers` / `actus health` |

## 目录结构

```
Actus/
├── README.md                  # 本文件：项目定位与总览
├── docs/                      # 设计文档（唯一书写源）
├── contracts/                 # 统一语义契约（action.schema.json 等）
├── actions/                   # 动作库存放（均为 .actus.md）
│   ├── ecosystem/  cli/  http/  demo/
│   ├── system/  text/  automation/
└── engine/                    # 执行核心（发现/校验/trust/执行/留痕）
```

## 许可

**Apache-2.0 单许可**：代码全部以 Apache License, Version 2.0 提供（见 `LICENSE`、`NOTICE`），可自由使用、修改、再分发与商用。商业版售卖的是**托管服务**（Actus Cloud），不售卖代码。动作是数据，不传染许可——第三方动作遵循其自身许可。

## 贡献

**"先搜开源，有→写动作，无→才进 builtin。"** 贡献规范见 [CONTRIBUTING.md](CONTRIBUTING.md)：一 PR 一事，写清文件范围与出口条件，`actus validate` 必须通过。
