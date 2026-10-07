# 网站维护记录

## Portfolio 图片恢复

记录时间：2026-10-06 19:20 PDT（America/Los_Angeles）。

已恢复 155 张独立照片和全部 16 张可见封面图。封面布局、顺序、数量、标题、地点、年份和 500px 作品链接保持原记录。相册改为直接加载本地展示图，公开源站返回的最长边为 1024 px。文件来源及尺寸见 `assets/img/portfolio/source-manifest.json`。

旧 `drscdn.500px.org` 图片链接返回 HTTP 403。新接口有 19 张照片返回空结果，其中 Tokyo 14 张、Kamakura 5 张，抽查 `1125124013` 原作品页面显示 `This photo is unavailable`。这些记录和旧嵌入路径暂时保留，恢复条件为用户提供对应原图或公开源站恢复。此项仍未完成，负责人为当前 Portfolio 修复任务。

验证：155 张 WebP 均能完整解码，除 image/image_large 之外的配置元数据、顺序和数量与修复前一致，Liquid 模板预览的 16 张封面均成功加载。Hawaii 相册打开及翻页通过，第 2 张照片直接从本地 WebP 加载。`git diff --check` 通过。本机完整 Jekyll 构建受系统 Ruby 缺失 `ruby/config.h` 阻塞，最终构建及发布由 GitHub Pages 验证。

## Git 与 checkout 台账

唯一 canonical checkout：`/Users/wenruixu/Documents/ruaruaxu.github.io`。权威仓库：`ruaruaxu/ruaruaxu.github.io`，default branch：`main`。

工作分支：`codex/restore-portfolio-photos`，owner：当前 Portfolio 修复任务，base：`c3ce071`，用途：恢复自托管展示图。未创建临时 checkout 或 worktree。通过 PR 验证及合并后将 canonical 同步到 main，历史分支的状态为 released - awaiting cleanup approval，复查触发为下一次网站维护。分支删除需单独批准。精确 HEAD 与 PR 合并证据以本任务交付记录为准。
