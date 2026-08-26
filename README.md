# Skyline Skill

面向 Codex 等支持 Agent Skills 的编码代理的微信小程序 Skyline 专项技能。

这个仓库把微信官方 [`wechat-miniprogram/skyline-skills`](https://github.com/wechat-miniprogram/skyline-skills) 中按主题拆分的 Skyline 资料整理为一个统一入口：代理只加载 `SKILL.md` 中的共用工作流，再按当前任务读取所需参考模块，减少多个相邻 Skill 同时触发和重复加载。

> 本仓库是非官方整合版本。涉及基础库版本、组件支持矩阵和 API 行为时，应以[微信官方 Skyline 文档](https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/skyline/introduction/)为准。

## 能力范围

- Skyline 架构、迁移、兼容与性能评估
- `app.json`、页面 JSON 和 `project.config.json` 配置
- Skyline 组件与滚动布局
- WXSS 支持与 WebView 差异
- Worklet、SharedValue 和交互动画
- 自定义路由、转场与返回手势
- ScrollViewContext 等滚动 API

## 目录结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── overview/
│   ├── config/
│   ├── components/
│   ├── wxss/
│   ├── worklet/
│   ├── route/
│   └── scroll-api/
├── UPSTREAM.md
└── LICENSE
```

## 安装

克隆仓库后，将仓库目录放到 Codex Skills 目录并命名为 `skyline`：

```bash
git clone https://github.com/yfpgle-glitch/skyline-skill.git ~/.codex/skills/skyline
```

新安装或更新后，新建一个 Codex 任务以加载最新 Skill。

## 设计边界

- Skyline 只在项目明确使用或计划迁移到 Skyline 时触发。
- 不因为理论性能优势就建议全局迁移，先检查实际项目配置和兼容风险。
- 不把本地参考快照当作最新官方事实。
- 编译、预览、上传和云端操作不属于本 Skill 的自动副作用。

## 来源与维护

上游来源、整合方式和同步规则见 [UPSTREAM.md](UPSTREAM.md)。仓库保留原项目的 MIT 许可证与版权声明。
