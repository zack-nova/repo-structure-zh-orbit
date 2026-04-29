<!-- orbit:begin orbit_id="repo-structure-zh-orbit" -->
# Git Repo Structure Orbit

这个 orbit 用来维护仓库的结构地图，让 Codex/agent 快速理解目录、关键文件、模块边界和职责说明。

用 `$sync-repo-structure-doc` 扫描真实目录并提出结构文档更新建议。默认建议目标为 `docs/repo-structure.md`；如果仓库已有明确结构文档路径，则沿用该路径给出建议。不要直接写入文件。

用 `$optimize-repo-structure` 分析大文件过长、职责混杂、层级不清、重复逻辑散落等结构问题；只输出建议、影响范围、最小下一步和验证方式，不直接移动文件、拆分模块、改 import 或写结构文档。

硬规则：分析前检查 git 状态；尊重用户已有改动；不要移动或修改生成物、依赖目录或 vendor 代码；任何结构改动都只作为建议列出，由用户另行确认执行。
<!-- orbit:end orbit_id="repo-structure-zh-orbit" -->
