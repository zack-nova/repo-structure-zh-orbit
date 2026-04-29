# Git Repo Structure 中文 Orbit

`github-repo-structure-zh-orbit` 是一个面向 Git 仓库的结构治理 orbit，负责让仓库目录结构始终“可读、可维护、可同步”。

## 内容

- `$sync-repo-structure-doc`：扫描真实仓库目录，提出 `docs/repo-structure.md` 或仓库既有结构文档的更新建议。
- `$optimize-repo-structure`：分析仓库结构问题，提出安全的小步结构重构建议和验证方式。

## 适合维护的文档

默认建议维护的结构文档：

```text
docs/repo-structure.md
```

## 作者检查

检查这个 source orbit：

```bash
hyard orbit validate
hyard orbit prepare github-repo-structure-zh-orbit --check
```
