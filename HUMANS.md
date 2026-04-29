<!-- orbit:begin orbit_id="repo-structure-zh-orbit" -->
# Git Repo Structure Orbit 使用说明

这个 orbit 帮助开发者维护仓库结构地图，并在结构开始失控时做小步整理。

## 常用方式

1. 同步结构文档建议：让 agent 使用 `$sync-repo-structure-doc`，扫描真实目录并提出 `docs/repo-structure.md` 或仓库指定结构文档路径的更新建议。
2. 诊断结构问题：让 agent 使用 `$optimize-repo-structure`，输出大文件、职责混杂、目录层级、重复逻辑和模块边界建议。
3. 规划小步重构：在建议明确后，让 agent 按 `$optimize-repo-structure` 输出低风险移动、拆分或 import 更新方案，并列出验证命令。

## 开发者确认点

读取和分析可以直接执行。这个 orbit 的 skill 不直接写文件、移动文件、拆分模块、改公共入口、删除旧路径或更新 import；这些操作需要用户另行确认执行。
<!-- orbit:end orbit_id="repo-structure-zh-orbit" -->
