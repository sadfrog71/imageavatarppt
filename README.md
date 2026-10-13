# imageavatarppt

所有风格统一使用 **ImageGen 生成完整页面**，包括标题、正文、数字、图表和背景。
最终 PPTX 每页是一张完整图片，文字不可逐字编辑。

## 使用流程

1. 先问并记录用户选择：港华风格、克制白底商务、自定义参考风格。已明确指定时不重复问。
2. 阅读材料、核对事实，确定逐页结论和版式。
3. 先生成 3 页确认稿（封面、一页看懂、第 3 页），自行看图后展示给用户。
4. 等待用户明确确认；修改意见处理完后再继续。
5. 锁定风格，复用前三页，生成其余页面并组装完整 PPTX。

总页数不足 3 页时，以实际全部页面为确认稿，不凑数。所有生成都使用 ImageGen；
不以无字背景加文字框、HTML 截图或其他图像模型替代。封面和结尾同样必须生成。

## 风格

- [港华风格](references/towngas-style.md)：浅冰蓝、深蓝标题、强调蓝数字、圆角卡片，Logo 先确认并使用用户正式素材。
- [克制白底商务](references/image-style-guide.md)：纯白底、有限强调色、证据与信息关系驱动布局。
- 自定义：根据用户实际参考图提取并锁定视觉规范。

## 组装

使用 [计划字段说明](references/deck-plan-schema.md)。`manifest.example.json` 为单页示例，
其中示例数字不构成任何实际项目事实，确认记录默认留空。

```bash
python3 scripts/validate_plan.py deck-plan.json
python3 scripts/assemble_deck.py deck-plan.json --preview
# 用户确认且全套图片就绪后：
python3 scripts/assemble_deck.py deck-plan.json
python3 scripts/audit_pptx.py deck-plan.json --output pptx-audit.json
```

旧版 provider、可编辑文字和模板脚本仅保留用于读取历史项目，不是新任务可选流程。
整页图中文字应通过看图核验；结构审计不能替代文字和视觉检查。

## Logo 素材

未提供或不确定时，先问是否需要 Logo。需要时请提供真实透明底 PNG，建议宽度
至少 1000px（或长边至少 1000px），保持原始比例；也可提供 SVG/PDF 矢量源。
默认建议显示宽度占页宽 8%–12%，实际按品牌规范与确认稿调整。
不自动生成标志或“Logo”字样；不放、留空位、可见占位均按用户明确选择处理。
