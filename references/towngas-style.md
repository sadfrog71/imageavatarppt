# 港华风格 / Towngas-style visual preset

## 定位与范围

面向高管汇报的克制、专业、结论先行的视觉模板。默认简体中文；每页一个核心
结论、一个主视觉焦点、2–4 条支撑信息。只提取设计倾向，不绑定具体企业资产、
案例、数字、人名、汇报对象、页数或叙事顺序。保留原技能的制作与审批流程，
不要求 runSkill、generateSlides、slidesCompose 或其他平台专用工具。

这是按需加载的视觉预设，不改变其他风格的外观。所有风格共同遵守 SKILL.md 的
ImageGen 整页生成合同：文字、数字、图表与背景一起生成；先选择风格，先出 3 页
确认稿，用户确认后生成剩余页面。正文等效 ≥20pt、标题等效 ≥28pt、图注等效
≥18pt。旧版原生可编辑文字和图片面积上限不适用。

## 固定设计规范

将以下六行作为整份汇报的共享视觉约束，预览与后续页面保持一致。
它们描述最终幻灯片；文字和背景均由 ImageGen 一起生成，不输出无字画布，
不在后期叠加正文。Logo 的处理须在生图前确认；选定素材作为真实参考图使用。

```text
Visual Thesis: a calm executive-briefing deck, modular information cards on light blue ground, conclusion-first composition with one dominant focal point per page, crisp flat vector rendering with rounded cards and bold flow arrows.
Palette: background pale ice blue #EEF4FB; primary text deep navy #12366B; secondary text slate #5A6B85; ONE accent blue #1E6FD9 for key numbers and highlights; sparing green #2BA36B / orange #F28C28 only for tiny status marks.
Typography System: Simplified Chinese by default; display titles in heavy, wide-set geometric sans with tight tracking and firm square stroke endings; key numbers oversized in accent blue; body in clean medium-weight humanist sans with generous line spacing; strict left alignment and consistent size steps.
Background / Texture: edge-to-edge pale ice blue, optionally with a very soft diagonal gradient to white where supported; no noise or patterns.
Media / Visual Treatment: original provided photos, screenshots, or illustrations inside rounded white-framed cards with soft shadows; flat vector diagrams with thick blue arrows that encode actual relationships; preserve source image content and never redraw faces or evidence.
Graphic Devices / Page Furniture: user-approved logo treatment at top-right (supplied asset, omission, or explicitly requested placeholder); thin navy rule under titles; small rounded number chips; footer metadata line in slate small type; no invented emblem or company wordmark.
```

用户指定语言时替换语言默认值，并在生成前锁定。其余页面不得自行换色、换字体
或改变页脚位置。修改单页只调整该页内容和版式，不漂移已锁定的视觉规范。

## 色彩、字体与页面秩序

| 用途 | 值 / 规则 |
|---|---|
| 背景 | `#EEF4FB`；可选极淡对角渐变至白色，不能形成装饰主视觉 |
| 标题、标题下细线、主文字 | `#12366B` |
| 辅助文字、页脚 | `#5A6B85` |
| 关键数字、重点、流程箭头 | `#1E6FD9`，唯一主要强调色 |
| 白卡片 | `#FFFFFF`，圆角、轻柔阴影 |
| 状态 | 绿 `#2BA36B` / 橙 `#F28C28`，仅小状态标记 |

不沿用原示例的大面积橙色下划线，以“绿橙仅作小标记”为准。标题粗重、字形
方正；正文中等字重，行距舒展。字体选择以本机可用中文字体为准；不为追求
窄字距挤压中文。主要文字左对齐；大数字允许按版式居中。保持统一边距、标题区、
页脚和层级。禁止赛博、霓虹、3D、深色科技风、彩虹色、纹理与装饰背景。

## Logo 确认与素材

- 先执行 SKILL.md 的“Logo 确认与交付要求”：不明确时询问是否需要并请用户提供正式素材，不自动写“Logo”。
- 首选真实透明底 PNG，建议宽度至少 1000px（或长边至少 1000px），保持原比例；也可提供 SVG/PDF 矢量源。白底或棋盘格截图不等于透明底。
- 页面显示宽度建议占页宽 8%–12%，等比缩放，遵守品牌安全边距；在确认稿检查位置与大小。
- 不放、留空位或显示占位字样按用户明确选择执行。不附带品牌链接、不搜索替代标志、不臆造企业字样。
- 正式素材先查看，再作为真实参考图交给 ImageGen，要求保留字形、颜色与比例；看图检查失真，不承诺像素级复现。
- 用户照片、截图和插画以原图置入圆角白框卡片，不满铺、不重画人脸、不改变
  界面证据。必要裁切不能丢失关键信息；人物姓名保持原字并对应具体人物。

## 八种版式

以下是唯一版式家族；根据信息关系选择，不能把整份汇报机械铺成相同卡片网格。
无足够信息时减少元素数量，不能为了凑版式编造指标、流程或证据。

| 版式 | 构图与适用内容 |
|---|---|
| 封面：左右分栏 | 左标题、副标题，可选中等尺寸团队图卡与对应姓名；右核心数字或核心判断、产品证据，下方最多 3 个真实指标卡；左下部门与日期 |
| 一页看懂 | 顶部最多 4 个真实指标卡，中部 3 步实际流程及粗箭头；底部一行已核实结论或状态，不默认写“已上线” |
| 左右对比 | 同口径过去/现在或人工/AI，左侧灰蓝弱化，右侧强调蓝；对应维度对齐 |
| 流程 | 3–5 步横向卡片，以粗蓝箭头表达顺序或因果；过长则拆页 |
| 大数字 | 一个主数字居中或偏左，旁边列算法、口径或依据，不用小字藏条件 |
| 网格 | 3–6 个同级内容卡片；有先后关系时改用流程，不能伪装成并列 |
| 路线图 | 横向时间轴、版本节点；仅在原稿或用户需要时使用，不强加未来计划 |
| 结尾 | 一句收尾结论与最多 3 个支撑点或行动；不写“谢谢观看” |

封面、转折页、结尾可加强字号对比；仍只保留一个视觉焦点。卡片、箭头是信息
关系的容器，不是装饰。八种版式容纳不了材料时，先拆页或与用户确认必要调整，
不删关键信息、不缩字号。

## 页面说明格式

在现有每页规划 / prompt 内使用以下结构，无需新增专用接口：

- `KEY CONTENT`：结论式标题、2–4 条支撑，建议 300 字以内。数字、单位、术语、
  人名和标准编号来自原稿；测算或预估明确标注。300 字不是删证据的理由。
- `VISUAL`：一个承载结论的图示或证据对象，说明素材位置、人物与姓名对应关系；
  原图使用 `faithfully reproduce, do not redraw faces, not full-bleed`，生成时必须
  传入实际原图并核对保真。写明用户已确认的 Logo 处理方式；未确认前不能生成。
- `LAYOUT`：以上版式名称、元素数量和阅读顺序。
- `TYPE ACCENT`（可选）：仅说明重点页需要放大的标题或关键数字。

事实矛盾先核实，不凭版式挑选一个数字；所有复用图片先看原图。

## 计划与脚本衔接

按 SKILL.md 与 deck-plan-schema.md 使用整页模式。设置语言 `zh-Hans`，palette：
primary/text `#12366B`，secondary/muted `#5A6B85`，accent `#1E6FD9`，
background `#EEF4FB`，`allow_nonwhite_background=true`。

ImageGen 整页路径支持本风格极淡对角渐变，使用 `background_mode=soft_gradient`；
也可统一选 `solid`，在确认稿前锁定。不能把旧提示词中的 no gradient background
与已经选定的极淡渐变同时发送；禁止纹理、装饰场景和抢眼渐变仍然有效。

不要混入旧模板的企业 Logo、页脚或原生封面/章节/结尾。全套页面都从 ImageGen
整页图片组装；图片内文字和 Logo 占位不可单独编辑。

## 验证要点

逐页检查结论、数字、原图、人名、Logo 占位、可读性与越界；联系表检查布局节奏、
色彩和页面家具一致性。卡片是本模板允许的语言，但避免机械重复。

同一生僻字最多重生成 2 次，仍有问题则列入人工核对清单，不自动用原生文本框
覆盖。安装模板不等于完成真实演示文稿视觉验证；最终制作仍须查看图片和 PPT。
