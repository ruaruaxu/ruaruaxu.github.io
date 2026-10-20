# 网站维护记录

## 首页太平洋居中 Equal Earth 地图

记录时间：2026-10-20 14:35 PDT（America/Los_Angeles）。

用户批准普通地图和 Satellite 共用太平洋居中的 Equal Earth 投影，并保留地点、路线、时间线、缩放和重置。`index.md` 使用 OpenLayers 10.11.0 与 Proj4js 2.20.9 替换 Leaflet，中央经线为 180°。两种底图共用一个 View，继续加载原 Esri 底图、卫星影像和标签。地图裁剪到单幅 Equal Earth 世界边界，避免横向重复。纬度范围沿用影像源的 Web Mercator 覆盖范围（约 ±85.05°）。

17 个地点的文字、原始经纬度、行程分组及三条迁移路线定义保持原样。地点、路线、点击定位和行程范围均使用同一投影。浏览器按视图分辨率加载并重投影瓦片。

验证：`git diff --check` 通过。临时 Node smoke 检查通过，包括内联 JavaScript 语法、17 个地点的投影往返、与原版本地点及路线定义的一致性、三条 97 点连续曲线的端点与标记对齐，以及仅一个共用 View。基于公开首页布局替换地图区块的本地预览已检查普通图、卫星图、Berkeley/Beijing 定位、日本行程、放大、缩小、重置和桌面/窄屏布局。全图预览中未观察到太平洋中央竖缝或重复世界，浏览器未报告地图 JavaScript 错误。尚未执行完整 Jekyll 构建，构建及上线验证待 GitHub Pages。

## Portfolio 图片恢复

记录时间：2026-10-06 19:20 PDT（America/Los_Angeles）。

已恢复 155 张独立照片和全部 16 张可见封面图。封面布局、顺序、数量、标题、地点、年份和 500px 作品链接保持原记录。相册改为直接加载本地展示图，公开源站返回的最长边为 1024 px。文件来源及尺寸见 `assets/img/portfolio/source-manifest.json`。

旧 `drscdn.500px.org` 图片链接返回 HTTP 403。新接口有 19 张照片返回空结果，其中 Tokyo 14 张、Kamakura 5 张，抽查 `1125124013` 原作品页面显示 `This photo is unavailable`。这些记录和旧嵌入路径暂时保留，恢复条件为用户提供对应原图或公开源站恢复。此项仍未完成，负责人为当前 Portfolio 修复任务。

验证：155 张 WebP 均能完整解码，除 image/image_large 之外的配置元数据、顺序和数量与修复前一致，Liquid 模板预览的 16 张封面均成功加载。Hawaii 相册打开及翻页通过，第 2 张照片直接从本地 WebP 加载。`git diff --check` 通过。本机完整 Jekyll 构建受系统 Ruby 缺失 `ruby/config.h` 阻塞，最终构建及发布由 GitHub Pages 验证。

## Git 与 checkout 台账

唯一 canonical checkout：`/Users/wenruixu/Documents/ruaruaxu.github.io`。权威仓库：`ruaruaxu/ruaruaxu.github.io`，default branch：`main`。

本机仅有上述 canonical checkout，无临时 checkout 或 worktree。分支删除需单独批准。

| 分支 | Owner / 用途 | Base / HEAD / upstream | 状态、证据与下一步 |
| --- | --- | --- | --- |
| `codex/restore-portfolio-photos` | Portfolio 修复任务 / 自托管展示图 | base `c3ce071`，HEAD `38b3cb07d51f38fbf20f6b1371f84e6347e6509d`，upstream `origin/codex/restore-portfolio-photos` | 2026-10-20 已复核 [PR #2](https://github.com/ruaruaxu/ruaruaxu.github.io/pull/2) 为 MERGED，合并提交 `eb2f0ca9025ae414db0bb5871c6e30c0381fe22d` 位于 main。无运行依赖，released - awaiting cleanup approval，负责人为网站维护任务，收到删除批准时重查。 |
| `codex/pacific-equal-earth-map` | 当前首页地图任务 / 同投影普通地图与卫星图 | base `eb2f0ca9025ae414db0bb5871c6e30c0381fe22d`，HEAD 待本次 coherent commit，计划 upstream `origin/codex/pacific-equal-earth-map` | 当前在唯一 canonical 路径实施，in use。下一步提交和 PR 审查，通过后合并并同步回 main，核实 Pages 发布。精确交付 HEAD 和 PR 以任务交付记录为准。 |
