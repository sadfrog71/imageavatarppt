# 整页 ImageGen 计划合同

使用一个 `deck-plan.json` 管理事实、风格、页面、生成和确认状态。
`manifest.example.json` 保留基础叙事字段供复用，示例事实不可用于真实汇报。
示例的风格未选择，因此直接校验会报告未确认；这是刻意设置的安全默认值。

## 必需工作流字段

```json
{
  "workflow": {
    "contract": "imagegen_full_deck_v1",
    "style": {
      "name": "港华风格",
      "confirmed": true,
      "selection_evidence": "填写用户真实选定风格的语句，不得代填假确认"
    },
    "preview": {
      "slide_ids": ["p01", "p02", "p03"],
      "status": "pending",
      "approval_evidence": ""
    }
  },
  "creative_brief": "受众、汇报目标、核心结论和素材边界",
  "design_constraints": "已选定风格的共享视觉规范，三页确认后保持不变",
  "include_cover": false,
  "include_catalogue": false,
  "include_closing": false,
  "typography": {"prefer_editable_text": false},
  "image_generation": {
    "provider": "openai",
    "model": "gpt-image-2",
    "composition_mode": "direct_imagegen_slide",
    "local_text_overlay": false,
    "max_image_area_ratio": 1.0,
    "background_mode": "solid"
  }
}
```

此处是字段片段，不是完整计划。模型名记录真实运行值；调用内置 ImageGen 时不
假设可控制工具未开放的模型/尺寸参数。禁止改用其他 provider 或无字底图工作流。

风格必须已由用户选定，`selection_evidence` 对应真实对话。`preview.slide_ids`
严格等于完整页序的前三页；不足三页时填写所有页。默认 `pending`，代理自行
看图通过不等于用户确认。用户明确认可后才填写 `approval_evidence` 并设为
`approved`。更改风格或整套设计规范后重置确认状态。

## 页面字段

保留现有 `sections` 数组，每项包含 `main_title`、`subtitle`、`slides`。
章节只是规划分组，不会自动插入分隔页。需要封面、目录、章节页或结尾时，显式
作为一张 slide 规划并交给 ImageGen 生成。

每页保留 id/title/message/claim_type/layout_type/image/exact_text 等基础字段，
以及受众问题、叙事角色、信息关系、素材来源、视觉焦点与前后衔接。完整字段可
参考示例；不要无故删除事实、来源和叙事记录。

- `title_render_mode`: 固定 `image`。
- `exact_text`: 包含标题在内的全部可见原文；测算值、单位、时间和来源图注完整。
- `image_area_ratio`: 固定 `1.0`，表示一张完整页面图；不再套用旧版 30% 限制。
- `editable_text`: 不设置，不叠加原生文字。
- `image`: 实际 ImageGen 产物的 PNG 路径，不能指向代码生成的示意图。
- `prompt`: 共享设计规范 + KEY CONTENT / VISUAL / LAYOUT；要求文字与背景一起生成。
- `source_asset_refs`: 用户实际素材，生成时通过工具真实引用，不只写入提示词。

`background_mode` 可为 solid；港华风格可用 soft_gradient（极淡对角渐变）。
非白底需 `allow_nonwhite_background=true`。规划颜色须与实际提示词一致。

## 校验边界

验证器检查模式、风格记录、前三页 ID、确认字段、禁止文字叠加和图片面积。
组装器 `--preview` 只读取前三页，写出独立的 `*-preview.pptx`；全稿组装在
pending 时拒绝运行。全稿只插入计划中的图片，不添加原生模板页。

这些记录无法独立证明用户真的说过确认，代理必须依真实对话填写。脚本也不能
证明 PNG 来源于哪种模型，须保留实际 ImageGen 工具产物与调用证据。未确认时
禁止生成剩余页，这是生成阶段的代理义务，不能靠组装拦截来代替。

结构审计检查单图页、页序和数量，不检验位图中文字的原生字号或可编辑性。
中文字、数字和图片保真须看图验证。旧 schema 仅供历史项目兼容，新任务不得
省略 workflow 来绕过这些要求。
