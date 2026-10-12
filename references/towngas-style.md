# 港华风格 / Towngas-style visual preset

## 定位与范围

面向高管汇报的克制、专业、结论先行的视觉模板。默认简体中文；每页一个核心
结论、一个主视觉焦点、2–4 条支撑信息。只提取设计倾向，不绑定具体企业资产、
案例、数字、人名、汇报对象、页数或叙事顺序。保留原技能的制作与审批流程，
不要求 runSkill、generateSlides、slidesCompose 或其他平台专用工具。

这是按需加载的视觉预设，不替换整个技能。未选择此模板时，沿用原默认设置。
正文、数字、标题、图注继续使用原生可编辑文字；正文通常 ≥20pt，标题 ≥28pt，
任何可见文字不低于 18pt。图片表达面积仍遵守原技能上限；较大的卡片、流程和
图表用原生形状构建。只有用户另外明确要求整页图片时才进入原技能位图路径。

## 固定设计规范

将以下六行作为整份汇报的共享视觉约束，预览与后续页面保持一致。
它们描述最终幻灯片；可编辑模式的图像生成请求仍须明确“无文字、预留文字区域”，
文字和 Logo 占位由原生排版补入，不能要求模型照着字体规范生成正文。

```text
Visual Thesis: a calm executive-briefing deck, modular information cards on light blue ground, conclusion-first composition with one dominant focal point per page, crisp flat vector rendering with rounded cards and bold flow arrows.
Palette: background pale ice blue #EEF4FB; primary text deep navy #12366B; secondary text slate #5A6B85; ONE accent blue #1E6FD9 for key numbers and highlights; sparing green #2BA36B / orange #F28C28 only for tiny status marks.
Typography System: Simplified Chinese by default; display titles in heavy, wide-set geometric sans with tight tracking and firm square stroke endings; key numbers oversized in accent blue; body in clean medium-weight humanist sans with generous line spacing; strict left alignment and consistent size steps.
Background / Texture: edge-to-edge pale ice blue, optionally with a very soft diagonal gradient to white where supported; no noise or patterns.
Media / Visual Treatment: original provided photos, screenshots, or illustrations inside rounded white-framed cards with soft shadows; flat vector diagrams with thick blue arrows that encode actual relationships; preserve source image content and never redraw faces or evidence.
Graphic Devices / Page Furniture: a neutral editable Logo placeholder fixed at top-right; thin navy rule under titles; small rounded number chips; footer metadata line in slate small type; no invented emblem or company wordmark.
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

## Logo 占位与素材

- 每页右上角保留同尺寸、同位置的中性 Logo 区，避开标题和安全边距。
- 默认用可编辑的 `Logo` 文本框及轻量占位框；不生成图徽、不写企业中英文名。
- 不附带品牌链接或远程参考图，不搜索或下载品牌标志，不将标志交给模型重画。
- 日后用户提供正式 Logo 且要求使用时，原图等比嵌入占位区，不拉伸、不改色。
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
  原图使用 `faithfully reproduce, do not redraw faces, not full-bleed`，实际组装仍
  优先原图嵌入。指定“右上角预留中性 Logo 区，不生成品牌标志”。
- `LAYOUT`：以上版式名称、元素数量和阅读顺序。
- `TYPE ACCENT`（可选）：仅说明重点页需要放大的标题或关键数字。

事实矛盾先核实，不凭版式挑选一个数字；所有复用图片先看原图。

## 与现有脚本的衔接

这是指导代理构建计划的模板，不是脚本自动识别的配置开关。把下列值写入现有
`deck-plan.json` 字段，保持原 schema 和 assembler 合同：

```json
{
  "language": {"primary": "zh-Hans"},
  "palette": {
    "name": "港华风格",
    "primary": "#12366B",
    "secondary": "#5A6B85",
    "accent": "#1E6FD9",
    "background": "#EEF4FB",
    "text": "#12366B",
    "muted": "#5A6B85"
  },
  "image_generation": {
    "background_mode": "solid",
    "allow_nonwhite_background": true
  }
}
```

这是合并片段，不是完整可执行计划；保留现有 provider、typography、sections 等
必要字段，以及来源保护词。现有验证脚本只支持 `solid`，因此默认采用浅冰蓝
纯色底；不传入未经支持的 gradient 模式。仅使用支持渐变的原生排版路径时，才
可添加极淡渐变，并如实检查最终呈现。

构建本模板提示词时，移除与选定圆角卡片冲突的泛化禁令，保留“禁止无意义重复”
和“箭头表达真实关系”。纯色路径继续保留 `no gradient background`；原生渐变
不交给该生成路径。`no logo` 指禁止模型生成品牌，原生 Logo 占位另行添加。

不要直接套用带其他品牌标志、企业页脚或“谢谢”结尾的旧模板。先检查模板母版、
封面、目录和结尾；按原技能允许的 blank/custom 路径使用统一页面家具，或最小
替换不兼容的元素。不得把旧品牌残留交付为本模板。

## 验证要点

逐页检查结论、数字、原图、人名、Logo 占位、字号与越界；联系表检查布局节奏、
色彩和页面家具一致性。圆角卡片是本模板允许的语言，不能仅因存在卡片就判失败；
仍应处理重复构图、无信息装饰或主次不清，不为过检查关闭全局审计。

可编辑文字有错直接修改文本。显式整页位图路径出现生僻字错误时，不反复重生成
超过 2 次；优先原生同字号覆盖修正，并列明人工核对项。此次安装模板不等于已完成
实际演示文稿渲染验证；最终制作仍需查看图片及 PPT 渲染结果。
