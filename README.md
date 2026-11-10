# 壁纸风格工作流

一个可跨 Agent 使用的壁纸创作 Skill：从视觉参考图中提炼风格系统，生成新主题壁纸提示词，并完成手机、平板、电脑及动态壁纸的逐步制作与验证。

GitHub：<https://github.com/weiyanxia52-cloud/wallpaper-style-workflow>

小红书 SkillHub：`壁纸风格工作流`（Skill ID：`104946`）

## 能做什么

- 分析多张参考图，区分风格特征与具体画面内容；
- 生成可复用的风格参考板提示词和负面提示词；
- 将新场景主题转译为结构化壁纸提示词；
- 在生图前确认模型、参考图策略、比例、成本与保存路径；
- 先迭代并确认手机版母版，再分别适配平板和电脑；
- 为已确认的静态壁纸设计低幅度、可循环的动态效果；
- 检查实际尺寸、格式、构图一致性与输出路径后再交付。

## 工作流程

```text
参考图
  → 风格诊断与风格参考板
  → 新主题壁纸提示词
  → 确认生成模型与路径
  → 生成并调试手机壁纸
  → 适配平板与电脑
  → 规划并生成动态壁纸
  → 验证与交付
```

工作流包含多个确认点，避免在风格、模型、母版或动态方案尚未确认时直接进入高成本生成。

## 安装

### Codex 与兼容的通用 Agent

```bash
git clone https://github.com/weiyanxia52-cloud/wallpaper-style-workflow.git \
  ~/.agents/skills/wallpaper-style-workflow
```

### Claude Code

```bash
git clone https://github.com/weiyanxia52-cloud/wallpaper-style-workflow.git \
  ~/.claude/skills/wallpaper-style-workflow
```

### WorkBuddy

```bash
git clone https://github.com/weiyanxia52-cloud/wallpaper-style-workflow.git \
  ~/.workbuddy/skills/wallpaper-style-workflow
```

其他宿主的已验证目录见 [`references/host-compatibility.md`](references/host-compatibility.md)。如果宿主提供官方 Skill 导入器，请优先使用官方导入方式。

安装后请重启或刷新 Agent，并确认它能够发现 `wallpaper-style-workflow`。

## 使用示例

上传一组壁纸或插画参考图后，可以这样开始：

```text
使用 $wallpaper-style-workflow 分析我上传的参考图。
先输出风格诊断、风格参考板提示词和负面提示词，不要立即生成图片。
```

继续制作新壁纸：

```text
沿用刚才确认的风格，制作“建在云端的图书馆城市”主题手机壁纸。
请先给出生成模型、参考图策略、比例和保存路径，等我确认后再生成。
```

## 默认画幅

未特别指定时，工作流会建议：

- 手机：`9:16` 竖版；
- 电脑：`16:9` 横版；
- 平板：`4:3` 横版。

这些是画幅建议，不代表固定像素尺寸。实际分辨率取决于所用模型和生成工具。

## 工具依赖

Skill 本身负责分析、决策、提示词、确认流程和结果验证。实际图片或视频生成取决于宿主 Agent 是否提供相应工具：

- 有图片生成工具：可以执行静态壁纸制作与迭代；
- 有图生视频工具：可以执行动态壁纸制作；
- 没有媒体生成工具：仍可输出完整、可迁移的提示词与制作方案。

模型名称、价格和能力可能变化，工作流会在执行前读取当前宿主的工具说明，而不是固定绑定某个模型。

## 目录结构

```text
wallpaper-style-workflow/
├── SKILL.md
├── README.md
├── LICENSE
└── references/
    ├── host-compatibility.md
    ├── model-routing.md
    ├── prompt-templates.md
    ├── style-analysis.md
    └── verification.md
```

## 更新

如果通过 Git 安装，可以在 Skill 目录执行：

```bash
git pull
```

## License

本项目采用 [MIT License](LICENSE)。
