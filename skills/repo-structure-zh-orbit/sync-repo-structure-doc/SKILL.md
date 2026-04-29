---
name: sync-repo-structure-doc
description: 扫描真实仓库目录并提出结构文档更新建议。为 docs/repo-structure.md 或仓库指定的结构文档生成内容草案、差异说明和人工合并建议；不直接创建或修改文件。
---

# Sync Repo Structure Doc

让结构文档反映真实仓库，而不是停留在记忆或猜测里。优先生成简洁、可扫描、可长期维护的结构地图建议。

## 目标文档

默认建议目标为 `docs/repo-structure.md`。如果仓库已有明确结构文档路径，则沿用该路径给出建议。不要直接创建、修改或删除文件。

如果现有文档带有以下托管区块，建议只更新区块内容，保留区块外手写说明：

```markdown
<!-- repo-structure:begin -->
<!-- repo-structure:end -->
```

建议新建文档时使用这个托管区块，方便后续安全同步。

## 扫描规则

1. 先读根目录 `AGENTS.md`、`README.md` 和 `docs/repo-structure.md`或已有结构文档。
2. 优先用 `git ls-files` 获取受版本控制的真实文件；需要包含未跟踪新文件时，再补充 `rg --files`。
3. 尊重 `.gitignore` 和项目约定。
4. 默认忽略：
    - `.git/`
    - `node_modules/`
    - `.venv/`、`venv/`
    - `dist/`、`build/`、`out/`、`target/`
    - `.next/`、`.nuxt/`
    - `coverage/`
    - `.cache/`、`.turbo/`
    - `__pycache__/`
    - 生成物、vendor 目录和大型二进制产物
5. 目录树保持简洁，通常限制到 3 到 4 层；对关键入口、配置、测试和文档可以单独列出。

## 文档结构

推荐生成以下章节：

```markdown
# Repository Structure

<!-- repo-structure:begin -->

Last synced: YYYY-MM-DD

## Directory Tree

## Directory Responsibilities

## Key Entry Files

## Module Boundaries

## Ignored Or Generated Paths

## Recent Structure Changes

<!-- repo-structure:end -->
```

内容要求：

- `Directory Tree`：展示主要目录和关键文件，不要把依赖、构建输出或缓存写进正文。
- `Directory Responsibilities`：用一句话说明每个主要目录负责什么；不确定时标注“待确认”，不要编造业务含义。
- `Key Entry Files`：列出应用入口、库入口、配置入口、脚本入口、测试入口和文档入口。
- `Module Boundaries`：说明模块之间应如何引用、哪些目录是公共入口、哪些是内部实现。
- `Ignored Or Generated Paths`：列出被忽略或不应由 agent 直接维护的目录。
- `Recent Structure Changes`：优先根据 `git status --short`、`git diff --stat`、最近提交或本轮移动记录总结；没有证据时写“未发现本轮结构变更”。

## 输出规则

- 只做只读扫描和建议输出，不直接写入、创建、删除或重命名任何文件。
- 输出建议前检查 `git status --short`，说明目标结构文档是否已有未提交修改。
- 如果目标文档有未提交修改，报告风险并给出人工合并建议，不生成会覆盖整篇文档的方案。
- 如果文档是手写且没有托管区块，建议追加托管区块或小范围更新对应章节，不建议整篇替换。
- 保持文档短小。结构文档服务于快速导航，不替代完整架构文档。
- 当用户另行完成新增、移动、删除目录后，建议同步结构文档里的树、职责、入口和忽略说明。

## 结束前

报告：

- 建议更新的结构文档路径；
- 主要建议新增或更新的章节；
- 扫描时忽略的关键目录；
- 任何无法确认的目录职责或需要人工补充的模块边界；
- 需要人工合并的内容草案或差异摘要。
