# Changelog

## 2026-10-12

### 新增

- 新增可选的港华风格视觉模板：浅冰蓝底、结论式标题、强调蓝数字及八种统一版式。
- 每页右上角保留中性、可编辑的 Logo 占位，不附带品牌图片、链接或企业字样。
- 关联技能入口、使用说明与设计指南，保留现有可编辑文字、来源保真及图片面积约束。
- 明确脚本采用浅冰蓝纯色底，极淡渐变仅用于支持它的原生排版路径。

### 验证

- 原示例计划与合并港华模板配置后的计划均通过验证。
- 检查六行共享视觉约束、入口链接与品牌 URL 排除；未调用付费生成，尚未进行实际 PPT 渲染验证。

## 2026-09-03

### Changed

- Default new decks to native editable PowerPoint titles and body copy, with an 18pt hard font floor and regular copy at 20pt or larger.
- Cap non-text raster and generated-image expression at 30% while keeping larger information systems editable.
- Strengthen source-evidence, semantic-visual-anchor, material-form, and result-evidence planning contracts.
- Extend plan, style, visual, and assembled-PPTX validation, including the new `scripts/audit_pptx.py` audit.

### Validation

- Python compilation, JSON parsing, plan validation, strict style audit, provider prompt dry-run, negative contract regressions, and skill-package validation.
