# 网站维护记录

## 首页太平洋居中满铺墨卡托地图（当前）

记录时间：2026-10-20 14:52 PDT（America/Los_Angeles）。

用户明确要求将 Equal Earth 改为满铺容器的墨卡托投影，默认从非洲和南美洲之间的大西洋切开，支持横向无限循环拖动，并恢复南极洲可见。`index.md` 的普通地图和 Satellite 共用原生 Web Mercator（`EPSG:3857`）。默认经度窗口为 −30–330°，中心为南纬 10°、东经 150°。默认和重置分辨率按矩形容器计算以铺满视口，初始最多显示一幅世界宽度。不同宽高比会裁切部分边缘范围，横向平移不设世界副本数量限制。纵向仍限制在原图源约 ±85.05° 的覆盖范围，墨卡托无法显示南极点。

保留 OpenLayers、Esri 底图及标签、地点、路线、时间线和缩放/重置。移除 Equal Earth 定义、曲边裁剪和 Proj4js 依赖。底图和路线启用横向 world wrap，HTML 地点标记随中心移动到最近世界副本，地点点击与行程选择也在最近副本中定位，同一行程作为整体平移。17 个地点的数据、三条路线定义及全部首页正文（包括读书与思考的新句子）保持原样。

验证：`git diff --check`，临时 Node smoke 检查（内联语法、17 个地点的投影往返、三条连续曲线、660×500 / 563×390 / 360×390 容器的满铺及横向循环、向东西各移动五个世界宽度时的地点副本定位、原始地点数据和全部正文一致性）。本地浏览器检查普通图、卫星图、跨整幅世界的连续拖动、循环后的地点/行程定位、重置及 390px 响应式布局。默认视图的非洲、南美洲和南极洲可见，未观察到中央竖缝。正式构建及发布由本次提交对应的 GitHub Pages run 验证。

此次为干净且已同步的 `main` 上的顺序小范围修订，无并行工作、未合并 PR 或新增任务分支/worktree。旧分支的已释放、待清理批准状态保持下方台账记录。

## 首页太平洋居中 Equal Earth 地图（历史，已被上述墨卡托方案取代）

记录时间：2026-10-20 14:35 PDT（America/Los_Angeles）。

用户批准普通地图和 Satellite 共用太平洋居中的 Equal Earth 投影，并保留地点、路线、时间线、缩放和重置。`index.md` 使用 OpenLayers 10.11.0 与 Proj4js 2.20.9 替换 Leaflet，中央经线为 180°。两种底图共用一个 View，继续加载原 Esri 底图、卫星影像和标签。地图裁剪到单幅 Equal Earth 世界边界，避免横向重复。纬度范围沿用影像源的 Web Mercator 覆盖范围（约 ±85.05°）。

17 个地点的文字、原始经纬度、行程分组及三条迁移路线定义保持原样。地点、路线、点击定位和行程范围均使用同一投影。浏览器按视图分辨率加载并重投影瓦片。

验证：`git diff --check` 通过。临时 Node smoke 检查通过，包括内联 JavaScript 语法、17 个地点的投影往返、与原版本地点及路线定义的一致性、三条 97 点连续曲线的端点与标记对齐，以及仅一个共用 View。基于公开首页布局替换地图区块的本地预览已检查普通图、卫星图、Berkeley/Beijing 定位、日本行程、放大、缩小、重置和桌面/窄屏布局。全图预览中未观察到太平洋中央竖缝或重复世界，浏览器未报告地图 JavaScript 错误。完整 Jekyll 构建由 [GitHub Pages run 39501894957](https://github.com/ruaruaxu/ruaruaxu.github.io/actions/runs/39501894957) 执行，2026-10-20 14:38 PDT 已观察到 `Build with Jekyll` 通过，最终构建及部署状态以该 run 为准。

交付代码：实现提交 `9c1221c161de8960c56a0b18cd5f099a710b5bf1`，经 [PR #3](https://github.com/ruaruaxu/ruaruaxu.github.io/pull/3) 于 2026-10-20 14:37 PDT squash merge 为 `892d0ad42b5c84d2fdf4cf78d5ddf58117e36ce4`。合并后已 fetch 并在唯一 canonical checkout 执行 `git pull --ff-only`，当时 `main` 与 `origin/main` 均为该合并提交且工作区干净。后续维护记录提交不改变地图实现。

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
| `codex/pacific-equal-earth-map` | 当前首页地图任务 / 同投影普通地图与卫星图 | base `eb2f0ca9025ae414db0bb5871c6e30c0381fe22d`，HEAD `9c1221c161de8960c56a0b18cd5f099a710b5bf1`，upstream `origin/codex/pacific-equal-earth-map` | [PR #3](https://github.com/ruaruaxu/ruaruaxu.github.io/pull/3) 已合并，`892d0ad42b5c84d2fdf4cf78d5ddf58117e36ce4` 已进入 main 并同步 canonical。无临时 checkout、作业、controller、automation 或恢复入口依赖该分支，owner 已释放，released - awaiting cleanup approval。负责人为网站维护任务，收到分支删除批准时重查。 |
