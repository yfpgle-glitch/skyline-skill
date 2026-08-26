---
name: skyline
description: 微信小程序 Skyline 渲染引擎开发与审查指南，覆盖 renderer 配置、迁移兼容、WXSS 差异、增强组件、Worklet 动画、自定义路由和滚动 API。Use when Codex works on a WeChat Mini Program that explicitly uses or plans to migrate to Skyline, or when the user mentions Skyline, worklet, SharedValue, draggable-sheet, custom-route, routeBuilder, open-container, enhanced scroll-view, or Skyline compatibility and performance.
license: Reference material derived from publicly available WeChat Mini Program documentation; verify current official terms before redistribution.
---

# Skyline 小程序开发

把本 Skill 当作 Skyline 专项参考，不要把它当成启用 Skyline 的理由。先检查项目现场，再决定是否使用 Skyline 特有实现。

## 工作流

1. 读取项目的 `AGENTS.md`、`app.json`、页面 JSON、`project.config.json` 和相关组件代码。
2. 确认当前页面使用 `webview`、`skyline` 还是混合渲染；不要擅自全局切换渲染器。
3. 按任务路由只读一个模块入口，再按入口指向精读 1～3 个细节文件。
4. 改动前列出 WebView/Skyline 行为差异、基础库要求、真机验证点和回退方案。
5. 实现后分别验证编译、模拟器和真机；涉及手势、滚动、原生组件、Worklet 或转场时，模拟器通过不等于真机通过。

## 模块路由

- 架构、迁移、兼容、性能与版本记录：读取 `references/overview/index.md`。
- `app.json`、页面 JSON、`project.config.json`：读取 `references/config/index.md`。
- `scroll-view`、`swiper`、`draggable-sheet`、`share-element`、`snapshot`：读取 `references/components/index.md`。
- Skyline 支持或限制的 WXSS/CSS：读取 `references/wxss/index.md`。
- `SharedValue`、`timing`、`spring`、`decay`、`runOnUI`、`runOnJS`：读取 `references/worklet/index.md`。
- 自定义路由、预设转场、返回手势、`open-container`：读取 `references/route/index.md`。
- `ScrollViewContext`、`DraggableSheetContext`、Worklet 滚动：读取 `references/scroll-api/index.md`。

## 强制边界

- 不因“性能更好”就迁移整个已发布小程序；先做单页试点和兼容审计。
- 不把 Web CSS 行为直接套到 Skyline；先查 WXSS 支持和布局差异。
- 不在未检查全部使用方时修改共享组件或全局 renderer 配置。
- 不凭本地快照断言最新基础库、支持矩阵或 API 行为。版本敏感信息须核对[微信官方 Skyline 文档](https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/skyline/introduction/)，无法联网时明确标注未实时验证。
- 不自动安装依赖、修改项目配置、编译、预览或上传；这些动作必须落在用户请求范围内，并按相应 WeChatIDE Skill 执行。

## 输出要求

说明当前渲染器、改动范围、兼容风险、使用的参考文件，以及需要 DevTools/真机验证的事项。引用本地参考时给出文件路径；引用版本事实时同时给出官方页面。
