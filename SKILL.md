---
name: imageavatarppt
description: Create executive PPT decks with mandatory ImageGen full-page images, including all text and backgrounds. Ask the user to select a visual style, generate three preview pages, wait for explicit approval, then generate the remaining pages and assemble the complete image-based PPTX. Supports 港华风格, restrained white executive style, and user-provided custom references.
---

# Image Avatar PPT

## 全局强制合同（所有风格）

1. **先确定风格**：用户未明确选定时，必须询问“港华风格 / 克制白底商务 / 自定义参考风格”。可附一句推荐理由，但不能代替用户选择。用户已明确指定则记录，不重复问。不能只问颜色就视为选定风格。
2. **整页由 ImageGen 生成**：标题、正文、数字、标签、图表、背景和页面家具一起生成。使用可用的内置 `image_gen` 工具，执行前读取 imagegen 技能。不得用代码绘图、原生文字、HTML 截图或其他模型替代整页生成。工具不可用时说明阻塞，不静默降级。
3. **先出 3 页确认稿**：默认封面、一页看懂、第 3 页。先自行逐页看图，再展示三页及联系表，询问风格、信息层级、文字、素材和已确认的 Logo 处理是否满意。总页数少于 3 页时展示全部实际页面，不凑页。
4. **确认后出全稿**：必须收到用户对这批确认稿的明确认可，才生成第 4 页及后续页面。用户此前说“直接全部生成”不能当作已看过确认稿；本技能仍保留该检查点。用户修改意见未处理完成时不继续。
5. **风格锁定**：确认后固定 `creative_brief`、`design_constraints`、字体层级、配色和页面家具。复用已确认的前三页，仅生成剩余页面；需要修改时只重生成受影响页。更换风格或整套视觉规范后重新展示确认稿。

这是全技能的新合同，取代旧版“默认可编辑正文、无字画布、文字叠加、图片面积 ≤30%、首张可选校准、原生模板封面/章节/结尾”等制作规则。旧脚本保留兼容历史计划，但新任务只能使用下述 `imagegen_full_deck_v1` 流程，不能走 legacy 路径。

## 风格入口

- **港华风格**：读取 `references/towngas-style.md`。浅冰蓝底、深蓝标题、强调蓝数字、圆角卡片和八种版式；Logo 按用户确认的素材处理，不内置品牌图片或企业字样。
- **克制白底商务**：读取 `references/image-style-guide.md`。白底、有限品牌色、证据和信息关系驱动版式。
- **自定义参考风格**：先查看用户参考图，提取六项共享规范：视觉主张、配色、字体、背景、素材、页面家具。不能只凭文件名猜风格。

每种风格均执行相同的整页生成、3 页确认和全稿流程。风格仅改变视觉规范，不改变生成方式。

## 事实与叙事

完整读取材料，建立 `facts.md`：核心结论、原始数字及单位/口径、术语、人名、版本、标准编号、时间、来源。数字冲突先问用户，不自行挑选。测算或预估明确标注，不编造缺失指标。保护原图和人物，不生成伪造的界面或证据。

管理层叙事读取 `references/executive-storyline.md`，沿用核心判断、受众问题、单页边界和页间衔接规则；其中任何原生文字或模板制作建议不得覆盖本合同。每页一个结论、2–4 条依据、一个主视觉。原稿放不下就拆页，不删关键信息或缩小成无法阅读的小字。路线图仅在材料或用户要求时出现。

先给出逐页大纲：结论标题、要点、版式。确认总页数和重要事实；页数以完整叙事为准，不为了模板凑数。已获授权的范围内直接推进，不重复索取授权。若另行调用付费服务，先核对已有授权是否覆盖具体服务与费用；不能通过换成其他图像模型绕开 ImageGen 要求。

## 计划与生成

读取 `references/deck-plan-schema.md`，以 `manifest.example.json` 为字段参考。所有页面（包括封面、目录、章节和结尾）都列入 `sections[].slides`，不允许组装器额外插入原生模板页。

新计划必须设置：
- `workflow.contract=imagegen_full_deck_v1`；记录用户风格选择及真实确认依据。
- `image_generation.composition_mode=direct_imagegen_slide`、`local_text_overlay=false`、`max_image_area_ratio=1.0`。
- `typography.prefer_editable_text=false`；每页 `title_render_mode=image`、`image_area_ratio=1.0`，不设置 `editable_text`。
- `include_cover/include_catalogue/include_closing=false`（这些页面已在 slides 中）。
- 所有可见文字含标题逐字列入 `exact_text`；源数字不改写。`prompt` 用 KEY CONTENT / VISUAL / LAYOUT / 可选 TYPE ACCENT 表达。

整页图以 16:9 生成，尽可能采用 2048×1152 或更高分辨率；如实际工具尺寸不同，记录真实尺寸并检查可读性，不能伪称达到目标。正文等效 ≥20pt，标题等效 ≥28pt，图注等效 ≥18pt；位图没有可审计的原生字号，以渲染可读性实检，不宣称通过原生字体检查。

生成提示词必须包含共享视觉规范、单页结论、逐字文字、信息拓扑、素材引用及内容边界。字体、布局、图表和背景都交给 ImageGen 完整设计，不要求“text-free canvas”。用户素材需查看后传给实际参考图接口，不能用文件名代替图像。Logo 未提供、版本不明或使用要求不确定时，先按下述规则询问；禁止自动画标志或放置“Logo”占位字样。

## Logo 确认与交付要求（所有风格）

- 生图前检查本次是否已经提供并明确选定 Logo。未提供、存在多个版本、配色或使用方式不确定时，一次询问：“这份 PPT 需要放 Logo 吗？如需要，请提供正式 Logo 文件；也可以明确选择不放或仅留空位。”已有明确选择不重复问。
- 需要 Logo 时告知文件建议：**首选带真实透明通道的 PNG，建议宽度至少 1000px（或长边至少 1000px），保持原始比例**；这是源文件清晰度建议，不是强制方形尺寸。支持提供 SVG/PDF 矢量源；生图工具不支持时，保留原件并等比转换为透明 PNG 参考图，不改变标志设计。品牌规范优先。
- 说明透明底要求：背景需真正透明，不能把白底或棋盘格当作透明底；不要提交截图、拉伸图或低清 JPEG。只有不透明图片时说明问题并请用户提供透明版本；未经授权不自动抠图、重画或改色。
- 区分源文件像素与页面显示尺寸：16:9 页面的右上角默认建议宽度约占页宽 8%–12%，高度随原比例缩放，留足安全边距；特殊长宽比例按品牌规范适配。确认稿中供用户检查大小与位置，不伪称存在官方固定尺寸。
- 等待素材时可继续整理内容与大纲，但不生成涉及未确定 Logo 的确认稿。用户明确选择“不放”则完全省略；明确选择“留空位”则只留空白；只有明确要求可见占位字样时才显示“Logo”。
- 正式素材需先查看，再作为实际参考图传给 ImageGen；在提示词中明确保留图形、颜色、比例和字样，并逐页看图核对。整页生图可能失真，不能承诺像素级复制；发现失真先报告，只修改受影响页，不以合成标志冒充原件。

## 两阶段执行

1. 风格已选择、大纲事实可用后，保存 `preview.slide_ids` 为前 min(3, 总页数) 页，`preview.status=pending`。
2. 仅对这些页面调用 ImageGen，保存原图并记录来源。自行查看全尺寸图，检查文字、数字、图表、人物和素材保真，再向用户展示。可以输出仅包含这些页的预览 PPTX；必须标明“确认稿”。
3. 等待用户明确确认。把真实确认语句记入 `preview.approval_evidence`，再设为 `approved`；不得自动填入“已确认”。等待、工具成功或代理自检均不构成用户确认。
4. 按锁定规范生成其余页。保持前三页原图不变，除非用户要求修改。每次图像调用后查看结果，仅修复失败页。
5. 形成完整联系表和逐页 QA。中文错字先报告，只重生成受影响页；同一生僻字最多重试 2 次，仍失败则列入人工修正清单。不能默认用文本覆盖来绕过整页生成要求。

旧 `generate_images.py` 为历史外部 provider 流程，新任务不用它生成图片。不得提前批量生成剩余页再伪装成等待确认。

## 组装与验收

```bash
python3 scripts/validate_plan.py deck-plan.json
python3 scripts/assemble_deck.py deck-plan.json --preview
# 只有用户确认后，且全部页面已生成并自检，才运行：
python3 scripts/assemble_deck.py deck-plan.json
python3 scripts/audit_pptx.py deck-plan.json --output pptx-audit.json
```

组装仅将每张 ImageGen 整页图铺入一页 16:9 PPT，保持图像完整，不额外插入原生标题、正文、章节、Logo 文本框或模板结尾。图片文字不可逐字编辑，交付时如实说明。

核对页面总数、顺序、每页单张全幅图、图像哈希与来源、前三页复用和确认记录。检查最终 PPT 渲染及联系表；脚本结构通过不等于中文和视觉通过。若渲染器不可用，明确说明。

交付：计划、事实清单、3 页确认稿、全套页面图、联系表、最终 PPTX、结构审计、人工核对清单。人工清单关注生僻字/人名、金额公式、标准编号、图表数字、原图与 Logo；不可编辑性不是缺陷或触发重新加文字层的理由。
