# 上游来源与整合说明

## 来源

- 官方仓库：<https://github.com/wechat-miniprogram/skyline-skills>
- 官方文档：<https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/skyline/introduction/>
- 2026-08-26 检查到的上游提交：`050bb071e091c2d0f7ac3e294f1e1514382b3978`

当前仓库是面向 Codex 的非官方整合版本，不声明与上述提交逐文件一致。

## 整合映射

| 上游 Skill | 本仓库入口 |
|---|---|
| `skyline-overview` | `references/overview/index.md` |
| `skyline-config` | `references/config/index.md` |
| `skyline-components` | `references/components/index.md` |
| `skyline-wxss` | `references/wxss/index.md` |
| `skyline-worklet` | `references/worklet/index.md` |
| `skyline-route` | `references/route/index.md` |
| `skyline-scroll-api` | `references/scroll-api/index.md` |

仓库根目录的 `SKILL.md` 是统一路由入口，负责现场判断、按需加载、变更边界和验证要求；各主题内容保留在 `references/` 下。

## 更新原则

1. 在临时目录获取上游更新，不直接覆盖当前仓库。
2. 按上表逐模块比较，保留本仓库的统一入口与安全边界。
3. 对版本敏感内容同时核对微信官方文档。
4. 运行 Skill 结构校验和引用路径检查后再提交。
5. 更新本文件记录的上游提交。
