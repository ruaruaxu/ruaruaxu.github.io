# 网站维护记录

## Portfolio 2023–2026 发布准备

记录时间：2026-11-01 16:41 PST（America/Los_Angeles）。

用户已明确回复“发布吧”，授权把当前审阅后的 Portfolio 内容发布至 GitHub 仓库 `ruaruaxu/ruaruaxu.github.io` 及 `https://wenruixu.com/portfolio/`。范围为 8 个新增条目与 66 张展示图片（19,641,582 bytes）、简短配文、lightbox 长说明显示修复，以及全体作品原始 PDF/PPT 入口移除。未发布源 PDF/PPT 或自行重做的图表。源图清单中的机器绝对路径已改为文件名，具体 PDF 页码、图像对象和编码信息保留。

发布前已刷新远端，canonical main 与 origin/main 均为 `840c9f38cd95e7333a7920d606503c7b813d6513`，无 open PR、无其他 checkout 或并行编辑。原 16 条作品数据、155 条原照片来源及 19 条待恢复照片记录均未改变。新增 8 条分别为 New Mexico、万里学院、红莲小学、赏徽栖乡、上生新所、跨界融城、高线驿站与屋中屋。全部新增图片完整解码、数据引用和相册数量检查通过，既有各作品浏览器预览验证记录见下方。完整构建由现有 GitHub Pages legacy main/root 发布流程验证，本机 Jekyll 依赖缺失限制保留。

本工作单元唯一任务分支为 `codex/portfolio-2023-2026`，owner 为当前网站维护任务，路径仍为唯一 canonical checkout `/Users/wenruixu/Documents/ruaruaxu.github.io`，base 为上述 main HEAD，预定 upstream 为 `origin/codex/portfolio-2023-2026`。用途仅为本次审阅和发布，无额外磁盘 checkout、运行任务或恢复入口。合并后回到 main 并快进同步，任务分支在确认合并后释放并等待用户另行批准删除。发布验证及最终同步证据将在收尾记录中补充。

## Portfolio 展示合同修订：已有成果与房地产财务重点（当前）

记录时间：2026-11-01 16:29 PST（America/Los_Angeles）。

用户明确要求：房地产竞赛封面不显示特等奖，获奖信息只写在点开后的说明中。预览不展示整份原 PDF，重点选择已有财务与商业分析成果。任何作品不提供原 PDF 打开或下载链接。用户进一步纠正：只展示他们已有的成果，不要求助手重做 PPT 或创作新图。今后本作品集默认仅进行策展、排序、必要的单图提取和简短说明，重画或重新创作须用户另行明确要求。此合同取代下方完整原稿预览、原 PDF/PPT 下载和早期建筑设计重点的相关记录。

房地产竞赛当前为 8 张：原第 25 页庭院内嵌图片继续作封面，加原 PPT 第 20 页客群与产品匹配、第 36 页可比项目定价、第 39 页财务假设与收入预估、第 41 页现金流与敏感性、第 42 页融资结构与成本、第 44 页风险管理、第 46 页分期运营。7 页均直接采用 LibreOffice 转换 PDF 的整页渲染，2560×1440，再编码为 WebP quality=85、method=6。保留原排版、原图表与原数字，不裁切、不重绘、不重新计算。原转换存在个别文字换行问题，也按已有成果保留。财务数字仍为竞赛方案预测，未将其写成已实现收益或独立审计结果。未采用税费关键指标第 40 页。封面及首图标题不带获奖信息，首图下方说明保留特等奖、队长 Wenrui Xu 和团队 Wondernova。

曾在临时目录自行重排商业图表，用户明确纠正后已弃用并移除这些临时新图，未将其加入网站或发布。本次最终文件均映射到原有成果及具体来源页码，见 `assets/img/portfolio/shang-hui-qi-xiang/source-manifest.json`。

从全体作品配置移除 PDF/PPT 的 `source_url`、文稿嵌入和下载入口，撤掉文稿模式及获奖角标代码。红莲小学、上生新所、屋中屋的现有图集内容保持原样，屋中屋的期刊 DOI 参考链接保留。网站发布目录中 5 份助手先前复制的源文件已逐字节核对并转存至 `/private/tmp/portfolio-source-archive/`：`honglian-primary-school.pdf`、`shangsheng-xinsuo-case-study.pdf`、`room-within-room-drawings.pdf`、`shang-hui-qi-xiang-competition.pdf`、`shang-hui-qi-xiang-original.ppt`。它们不再是网站部署内容，用户提供的 Downloads、微信文档和 ZIP 原件均未改动。相关 manifest 与图片 README 已更新为不公开原件的当前状态。

验证：Liquid 4.0.4 渲染、Node 内联脚本语法、8 张原图的完整解码/原渲染尺寸/具体来源页/精确库存、全体作品原文件链接缺失、5 个撤回副本存在，以及 `git diff --check` 均通过。Chrome 确认获奖角标数量为 0，奖项只出现在打开后的首图说明，8 张原页逐张成功加载、caption 位于视口内，红莲小学源文件按钮隐藏且无 href。全体卡片无 PDF/PPT 地址。保存原现金流第 5/8 张与无角标卡片预览。完整 Jekyll 构建仍未验证，沿用既有依赖缺失限制。

同步状态：唯一 canonical `/Users/wenruixu/Documents/ruaruaxu.github.io`，main / origin/main 缓存 HEAD 均为 `840c9f38cd95e7333a7920d606503c7b813d6513`，全部工作为同一已批准本地 Portfolio 工作单元，未 commit、push 或发布。无新增 branch/worktree，旧分支仍为下方台账的 awaiting cleanup approval。临时预览服务器在验证后关闭。

## 2025 万里学院余姚校区：景观与教学楼设计

记录时间：2026-11-01 16:03 PST（America/Los_Angeles）。

用户提供《硕士学位论文答辩PPT_徐文睿 2023210060(1).pdf》，指定作为 2025 作品，重点展示万里学院景观设计和教学楼效果。原 PDF 为 70 页、50,159,881 bytes，创建于 2025-05-18。本次仅整理设计作品，不新增研究结论或学术成果说明，不把整套答辩 PDF 或幻灯片截图放入网站。

最终精选 12 张：第 61 页庭院水池与环廊作封面，第 55 页一期校园总鸟瞰、第 56 页景观总平面、第 59 页西入口鸟瞰与格物广场、第 60 页南入口树阵、第 61 页中心绿地鸟瞰、映月池和竹荫，以及第 63 页智能制造教学楼外观、教学中庭与产业工程师学院概念外观。按“建筑与景观关系 → 校园整体 → 公共空间 → 教学楼外观与室内”组织，既有通用图库和功能不重复扩展。未采用外部参考案例、重复楼层平面、宿舍外观或整页材料。

工作参与依据为第 44 页明确列出的“配合项目组进行校园规划调整深化、参与景观规划和专项设计、负责主要景观节点空间塑造”。网页据此说明参与规划及景观工作、负责重要景观节点，不补写校园整体独立作者或建成事实。选入的景观图在源页标为自绘，教学楼概念来自第 63 页。第 51 页标注“来源项目组”的总鸟瞰未使用。

图像通过 pypdf 提取内嵌原图，pdfplumber 记录页面位置和 PDF 对象 ID。完整保留单图、不裁切、不放大，最长边 2560 px，WebP quality=85、method=6。12 张共 6,384,846 bytes，具体来源和尺寸集中记录于 `assets/img/portfolio/wanli-university/source-manifest.json`。用户原 PDF 保持原样，未复制入网站仓库。

用户同时明确确认：所发截图用于上一项高线驿站封面，万里学院从新 PDF 选封面。高线驿站继续使用既有高分辨率 `overall-axonometric.webp`，确认写入其来源清单，未用低清截图替换。

验证：Liquid 4.0.4 渲染通过，12 张图片完整解码、配置与来源清单的数量/顺序/尺寸/字节大小/精确库存/无放大检查通过，封面及年份一致，`git diff --check` 通过。Chrome 本地逐张检查 1/12 至 12/12，图片均加载、说明均在视口内，保存封面、教学楼外观、中庭和 2025 卡片预览。沿用既有主题编译 CSS 进行本地模板预览，完整 Jekyll 构建尚未通过验证，既有依赖限制不变。

同步状态：本次继续同一已批准的本地 Portfolio 工作单元。唯一 canonical `/Users/wenruixu/Documents/ruaruaxu.github.io`，main / origin/main 缓存 HEAD 均为 `840c9f38cd95e7333a7920d606503c7b813d6513`，全部修改保留本地，未 commit、push 或发布。无新增 branch/worktree，旧分支继续保留下方台账的 awaiting cleanup approval 状态。已关闭本次预览服务器，无新增运行依赖。

## 2023 跨界融城规划与高线驿站建筑设计：精选拆图

记录时间：2026-11-01 16:00 PST（America/Los_Angeles）。

用户提供 `1953424-徐文睿-建筑学(四)-展览展板.pdf`，要求作为 2023 作品、拆图展示，并明确其中包含规划设计和口岸综合体建筑设计。单页原 PDF 为 37,713,388 bytes，展板署名徐文睿、指导教师陈泳和谭峥，标题为“跨界融城——深港皇岗口岸边界空间重构”，建筑部分为“高线驿站——福邻口岸与跨境酒店教培综合体”。原 PDF 保持原样，未复制进网站，也未启用海报预览或下载。

按用户后续“普通、信息量低的图不要放”要求，最终由初选 18 张精简为 10 张。规划项保留一张高质量鸟瞰、功能布局和交通系统，共 3 张。建筑项保留整体轴测、一层平面、剖透视，以及街角、下沉街道、换乘站和教培中庭，共 7 张。去掉重复且分辨率较低的另一张鸟瞰、四张基础策略示意、二至四层重复平面和低对比地下平面叠图。地下空间由完整剖透视表达，未声称地下平面被保留在提取后的剖面图中。

两项分别归入 2023，均使用双列宽封面。图像直接由 `pdfimages` 提取，保留完整单图、无裁切、不放大，最长边 2560 px，WebP quality=85、method=6。10 张共 4,142,916 bytes，来源、内嵌图索引、尺寸和顺序分别记录于两个目录的 `source-manifest.json`。网站英文短配文以“城市功能与交通整合”和“复合功能、竖向空间及空间体验”分别组织，不补写奖项或建成事实。初选后未采用的 8 张本次生成文件已移除，用户原件未改动。

验证：Liquid 4.0.4 渲染通过，精选配置、精确图片库存、完整解码、尺寸、无放大、来源清单及 `git diff --check` 检查通过。Chrome 初选时逐张核对图片与 caption 在视口内，精选后重载验证卡片 3/7 数量、建筑封面和第 3/7 张剖透视、修改后的配文与顺序，保存精选后预览。完整 Jekyll 构建仍受既有依赖缺失限制，本次未声称完整构建通过。

同步状态：唯一 canonical `/Users/wenruixu/Documents/ruaruaxu.github.io`，main / origin/main 缓存 HEAD 均为 `840c9f38cd95e7333a7920d606503c7b813d6513`，当前工作区为同一已批准 Portfolio 工作单元的本地修改，未 commit、push 或发布。本次未新建 branch/worktree，旧分支继续保留下方台账的 awaiting cleanup approval 状态。

## 赏徽栖乡：特等奖与完整原稿预览（历史，已撤销）

记录时间：2026-11-01 15:52 PST（America/Los_Angeles）。

用户明确补充比赛获“特等奖”，并要求将粗糙的摘图预览改为原始 PPT 展示。现卡片显示金色“特等奖 · Grand Prize”标识，查看器标题及说明也写明特等奖，保留 Team leader: Wenrui Xu / Team: Wondernova，不列具体分工。获奖依据为用户本次明确陈述，未独立查验证书或官网公告。

本方案替代下方 8 张精选展示。点击卡片进入完整 49 页文稿模式：网页通过浏览器 PDF 查看器展示从原 PPT 转换的全部幻灯片，默认整页缩放，支持原生页码跳转与缩放。页面同时提供 Open presentation PDF 和 Download original PPT。旧版 `.ppt` 原件原样复制为 `assets/files/portfolio/shang-hui-qi-xiang-original.ppt`（90,562,560 bytes，约 86 MiB），与用户输入逐字节一致。PDF 预览保留幻灯片内容，不包含 PowerPoint 原生动画或编辑功能。未上传到外部 Office/Google 查看器。

修正转换 PDF 元数据中的通用模板名和占位作者，预览标题为“赏徽栖乡 — 特等奖 | Wondernova”，作者为 Wondernova。当前 PDF 为 13,454,994 bytes。修改前后 49 页内容流逐字节一致，页框序列化最大差异约 1.89e-7 pt，封面重渲染与修改前逐像素一致。原 PPT 元数据和内容均未改动。

配置通过 `document_url` 启用文稿模式，保留普通照片相册流程。查看器在文稿模式中使用原生 PDF 导航并隐藏图片翻页按钮，关闭后释放 iframe。原先 7 张摘图 WebP 已移除，仅保留庭院封面 `vision.webp`。来源清单同步记录获奖依据、完整预览方式、原 PPT 路径及 PDF 元数据调整。

验证：Liquid 4.0.4 渲染、Node 内联 JavaScript 语法检查、49 页配置/特等奖字段/原 PPT 逐字节一致/精确封面库存检查、PDF 内容流及封面渲染比较，以及 `git diff --check` 均通过。Chrome 本地预览确认 1/49 封面完整显示、跳转第 11 页客群定位、特等奖与队长说明、PDF/PPT 链接。关闭文稿后复查 NM 仍定位到 8/16，普通图片、翻页按钮和 download 属性复位正常。最终预览图见本任务临时输出。完整 Jekyll 构建限制延续历史记录。

状态：所有 Portfolio 修改继续保留在本地 canonical main，尚未 commit、push 或发布。原 PPT 现为计划发布内容的一部分，须随最终内容一起经用户明确确认后才能对外上传。无新增分支或 worktree。

## Portfolio 新增 2024 赏徽栖乡竞赛方案（历史，8 张精选已被完整原稿预览取代）

记录时间：2026-11-01 15:45 PST（America/Los_Angeles）。

用户提供《房地产大赛终稿PPT.ppt》，要求作为 2024 作品，并明确说明自己是队长、不必列具体分工。封面核实项目名为“赏徽栖乡”，团队 Wondernova，赛事为第三届全国高校房地产创新创业邀请赛。网页标注 Team leader: Wenrui Xu / Team: Wondernova，以团队竞赛方案组织叙事，未推断个人逐项分工或奖项。2024 为用户指定的作品集分组年份，源 PPT 内嵌最后保存日期为 2021-10-22，保留于来源记录。

原件为约 86 MB 的旧版二进制 PPT。使用本机 LibreOffice 26.2.2.2 的 headless impress_pdf_Export 转为 49 页预览 PDF，并检查全部幻灯片缩略图。仅将转换后的完整方案 PDF 放入 `assets/files/portfolio/shang-hui-qi-xiang-competition.pdf`（13,443,318 bytes），未将原 PPT 加入仓库。原 PPT 保持原样。该 PDF 为格式转换副本，并非与原 PPT 逐字节相同的文件。

沿用用户的精选与叙事要求，最终选择 8 张：第 25 页庭院场景为封面，第 11 页客群定位、第 18 页总体规划图、第 21 页主力户型、第 22 页立面效果图、第 23 页步行街场景、第 36 页市场比较定价、第 46 页分期发展。以“客群定位 → 空间产品 → 定价与开发运营”串联方案，说明中标明价格为竞赛提交方案的建议值，未把预测、开发阶段或营收数字表述为已实现结果。图像直接提取自转换 PDF 的内嵌原图，4 张分析页以最长边 2560 px 渲染，均采用 WebP quality=85、method=6，8 张共 1,925,820 bytes，未放大源图。封面源图为 864×486 px。来源页码、转换方式、队长身份依据及图片编码参数见 `assets/img/portfolio/shang-hui-qi-xiang/source-manifest.json`。

验证：Liquid 4.0.4 模板渲染、Python 图片完整解码/尺寸/来源页码/配文/文件大小一致性检查、网站 PDF 与转换副本逐字节比较、既有新增作品设置检查，以及 `git diff --check` 均通过。本地浏览器核对 2024 卡片、1/8 队长说明、8/8 分期发展、源 PDF 页链接及 caption 位于视口内，保存 2024 分组预览。完整 Jekyll 构建依赖缺失的限制延续下方记录，未声称在 PowerPoint 中验证。

交付状态：与此前 Portfolio 新增项同属唯一 canonical main 的本地待审阅工作单元，尚未 commit、push 或发布，无新增分支/worktree。

## Portfolio 新增 2023 屋中屋：精选叙事

记录时间：2026-11-01 15:39 PST（America/Los_Angeles）。

用户要求把“屋中屋”归入 2023，提供最终模型照片目录、10 页最终图纸及胡滨的《建筑学报》文章，并说明作品收录于胡滨著《建筑设计教学档案》。随后明确要求精选好看的内容、讲好故事、突出能力，并要求书籍说明不写页码。最终作品集采用 8 张精选（3 张模型照片、5 张图纸/场景板），按场地与地形 → 公私流线 → 平面与剖面 → 剖切模型 → 广场与书吧体验组织。每张配 claim-first 的简短说明，分别展示场地回应、空间组织与推敲、视觉表达。完整图纸作为补充 PDF，不在主相册中堆放全部材料。

封面来自 `最终模型照片/1：100/总体2.jpg`，与《建筑学报》图 10 中的整体模型一致，未裁切。其余精选为图纸第 1、4、3、7、8 页，以及 1：50 的“剖面 楼梯间与阁楼的家”和“剖面 局部 乡村书吧、地穴公共客厅”模型照片。8 张 WebP 共 1,859,022 bytes，quality=85、method=6。模型图最长边 1920 px，图纸由 `pdftoppm -scale-to 2560 -png` 渲染后转换。未选中的 32 张本次生成 WebP 已移除，用户原始目录保持原样。原 10 页 PDF 原样保存到 `assets/files/portfolio/room-within-room-drawings.pdf`（24,320,648 bytes）。来源、顺序和出版证据集中记录于 `assets/img/portfolio/room-within-room/source-manifest.json`。

出版证据：用户提供的胡滨《以议题启动的设计教学法研究》，《建筑学报》2023(03): 32–40，DOI `10.19819/j.cnki.ISSN0529-1399.2023030007`，印刷第 39 页图 10 明确展示该作品并署名“徐文睿，2021年”。网页准确表述为作品 featured in 胡滨的文章，未将用户写成该文章作者。2023 为用户指定的作品集分组年份，作品设计年份 2021 保存在来源记录。文章不作为整篇副本放入网站，提供 DOI 链接。

书籍信息通过高校图书馆书目及书商记录核对为：胡滨著，《建筑设计教学档案：以议题开启的设计教学实践》，同济大学出版社，2024，ISBN 9787576513462。书目链接：`https://jp.tfswufe.edu.cn/opac/book/554aad2951af3fed9c6830982fcb5376`。作品被书收录的依据是用户本次明确陈述，未独立查阅书内页面。按用户要求不展示书籍页码，网页采用简短出版说明。

查看器增加可选 `blog_label`，本作品显示 View journal article，原博客链接默认 Read blog。修复本次观察到的长说明溢出：figure 改为两行 Grid，在可用高度中给图片和自然高度的 caption 分配空间，图片保持 contain。桌面 8 张精选的说明均在视口内，390×844 窄屏首尾内容可见。复查 NM 封面仍定位到 8/16，原 source 标签与隐藏博客链接状态正常。

验证：Liquid 4.0.4 渲染、Python 精选清单/图片解码/尺寸/来源/精确资产库存检查、原图纸 PDF 逐字节一致性检查、Node 内联脚本语法检查及 `git diff --check` 均通过。浏览器核对 8 张顺序、独立说明、图纸及期刊链接、桌面与窄屏布局。完整 Jekyll 构建依赖缺失的限制延续下方记录。此项与 NM、红莲小学、上生新所同属本地待审阅工作单元，唯一 canonical main 尚未 commit、push 或发布，无新增分支/worktree。

## Portfolio 新增 2024 上生新所案例分析

记录时间：2026-11-01 15:30 PST（America/Los_Angeles）。

用户提供《上生新所-徐文睿.zip》，要求作为案例分析作品加入 Portfolio，随后将年份从 2025 更正为 2024。新增 Shangsheng Xinsuo Case Study，卡片显示 Shangsheng Xinsuo，类型为 Urban Design Case Study，地点为 Changning, Shanghai, China。原 PDF 标注“绘图分析：徐文睿”，网页据此使用 Drawings and analysis by Wenrui Xu，未将该项表述为用户设计建成的项目。2024 为用户指定的作品集分组年份，源文档创建时间仍记录为 2023-08-14。

压缩包约 1.3 GB，含大型 PSD、Rhino、CAD 和 InDesign 源文件。本次仅提取其中唯一 PDF（11,917,307 bytes）及 `Links/4 建筑尺度-平面.jpg`，未将压缩包或大型源文件放入网站。原 PDF 原样保存为 `assets/files/portfolio/shangsheng-xinsuo-case-study.pdf`。PDF 第 1 页为空白，网页按原序展示第 2–7 页的 6 个内容跨页，并通过 View PDF 指向对应原页。源 PDF 的页脚占位文字保持原样。

封面采用入口广场建筑尺度平面原图，原尺寸 9448×10629 px，等比例缩至最长边 1800 px，未裁切。内容页通过 `pdftoppm -f 2 -l 7 -scale-to 2560 -png` 渲染后转为 WebP，7 张 WebP 共 2,724,354 bytes，quality=85、method=6。来源成员名、原页码、空白页处置及编码参数集中记录于 `assets/img/portfolio/shangsheng-xinsuo/source-manifest.json`。

验证：Python smoke 检查通过，覆盖 2024 分组、6 个内容跨页、源页对应关系、全部 WebP 解码、尺寸及来源清单一致性、PDF 与压缩包提取原件逐字节一致，确认红莲小学仍归 2025、NM 仍跨两列。Liquid 4.0.4 模板渲染通过，本地浏览器检查封面、首个内容跨页加载、首尾翻页及 PDF 页链接，已保存 2024 分组预览。`git diff --check` 通过。完整 Jekyll 构建依赖缺失的限制延续下方记录。

交付状态：与 NM、红莲小学属于同一待审阅的 Portfolio 本地修改工作单元，保留在唯一 canonical checkout 的 main。尚未 commit、push 或发布，无新增分支或 worktree，等待用户明确批准最终内容上线。

## Portfolio 新增 2025 红莲小学设计作品

记录时间：2026-11-01 15:16 PST（America/Los_Angeles）。

用户要求将《红莲小学.pdf》作为一个作品放入 2025 分组，并明确指定第一页的模型照片作为封面。新增 Honglian Primary School Renovation，卡片显示 Honglian Primary School，类型为 Architectural Design，地点为 Xicheng, Beijing, China。2025 是用户指定的作品集分组年份。文件中的 2022.12 调研、2023.11 方案、2024.08 南侧照片和 2024.09.01 开学典礼时间保留在页面或说明中，未将其改写为 2025 年建成。

原 PDF 原样保存到 `assets/files/portfolio/honglian-primary-school.pdf`（16,984,596 bytes）。封面由 `pdfimages -f 1 -l 1 -j` 直接提取第一页 object 7 0 的模型照片（2242×1495 px），等比例缩至 1600 px 宽，未裁切。4 页通过 `pdftoppm -scale-to 1920 -png` 渲染后转换为 WebP，点击卡片显示完整第一页并可顺序浏览 4 页，View PDF 链接指向对应 PDF 页。5 张 WebP 共 1,217,948 bytes。来源和编码参数见 `assets/img/portfolio/honglian-primary-school/source-manifest.json`。

验证：Python smoke 检查覆盖 2025 分组、4 页配置、封面匹配、全部展示图解码、尺寸和来源记录、PDF 与用户原件逐字节一致，以及 NM 仍跨两列。Liquid 4.0.4 模板渲染通过。本地浏览器检查模型封面、打开第一页、连续翻至第 4 页及各页 PDF 链接，已保存 2025 分组预览。`git diff --check` 通过。完整 Jekyll 构建依赖缺失的限制延续下方记录。

交付状态：此项与 NM 属于同一待审阅的 Portfolio 本地修改工作单元，保留在唯一 canonical checkout 的 main。尚未 commit、push 或发布，无新增分支或 worktree，等待用户明确批准最终内容上线。

## Portfolio 新增 2026 New Mexico

记录时间：2026-11-01 15:07 PST（America/Los_Angeles）。

在 2026 分组首位新增 New Mexico，保留公开相册 `https://500px.com/gallery/azrKStBezvH` 的 16 张照片及顺序。用户指定封面为 `https://500px.com/photo/7GwHTEsTj19`，本地文件为 `assets/img/portfolio/500px-3001241600.webp`。沿用现有 lightbox，打开时定位到封面（源相册第 8 张）。照片原题均为 Untitled，地点使用 New Mexico, USA。

用户随后要求放大 NM，已设置 `layout_span: 2`，保留原比例。桌面预览中 NM 与 Hawaii 同宽、上下排列，Mount Diablo 与 Point Reyes 位于右侧。浏览器实测 NM 宽约 649 px，普通单列卡片宽约 319 px，图片加载成功。

图片来自公开相册已渲染的展示图，16 张 WebP 共 1,264,024 bytes，最长边 1024 px，quality=85、method=6，未放大。逐图来源、尺寸和文件大小写入 `assets/img/portfolio/source-manifest.json`，临时签名图片 URL 未写入网站配置。此项不涉及原有 Tokyo/Kamakura 19 张待恢复照片。

验证：`git diff --check` 通过。临时 Python smoke 检查通过，覆盖 16 张图的完整解码、封面、数量、源链接、尺寸、aspect 和来源清单一致性，并确认原有相册配置及原来源记录未变。使用锁定版本 Liquid 4.0.4 渲染当前模板，本地浏览器确认卡片显示、封面定位、下一张图片加载及源链接。预览使用现有编译主题 CSS。本机 `bundle check` 显示 Jekyll 构建依赖缺失，因此尚未验证完整 Jekyll 构建。

交付状态：用户批准本地修改，当前变更位于唯一 canonical checkout 的 main，尚未 commit、push 或发布，等待用户审阅并明确批准上线。未创建分支或 worktree。远端及修改前本地 main 为 `840c9f3`。2026-11-01 已复核下方两个旧任务分支的 PR 均已合并，合并提交可从 main 到达，无开放 PR。旧分支继续保持 released - awaiting cleanup approval，不在本次修改范围内。

## 首页太平洋居中满铺墨卡托地图（当前）

记录时间：2026-10-20 14:54 PDT（America/Los_Angeles）。

用户明确要求将 Equal Earth 改为满铺容器的墨卡托投影，默认从非洲和南美洲之间的大西洋切开，支持横向无限循环拖动，并恢复南极洲可见。随后用户提供参考截图，要求以欧洲—亚洲—太平洋—北美及中美路线为主体，缩小南极洲在默认视图中的占比。`index.md` 的普通地图和 Satellite 共用原生 Web Mercator（`EPSG:3857`）。默认经度窗口为 −30–330°，目标中心为北纬 20°、东经 150°（取代尚在本次迭代中的南纬 10° 设定）。南极洲在默认桌面视图底部少量露出，可继续向下拖动查看。默认和重置分辨率按矩形容器计算以铺满视口，初始最多显示一幅世界宽度。不同宽高比会裁切部分边缘范围，横向平移不设世界副本数量限制。纵向仍限制在原图源约 ±85.05° 的覆盖范围，墨卡托无法显示南极点。

↻ 恢复上述默认中心和按当前容器尺寸计算的默认缩放。先取消已有移动/缩放动画并更新最小缩放，再启动恢复动画，避免之后的缩放约束更新中断恢复过程。地点选择和底图类型继续保留，重置操作只恢复地图视图。

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
