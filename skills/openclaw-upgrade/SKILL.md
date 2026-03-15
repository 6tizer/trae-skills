---
name: "openclaw-upgrade"
description: "OpenClaw 版本升级助手，完成升级、生成中文 changelog、识别遗漏功能。当用户说'升级OpenClaw'、'OpenClaw更新'、'检查OpenClaw升级内容'、'生成OpenClaw更新日志'或'帮我升级OpenClaw'时调用。"
---

# OpenClaw 升级助手

## 目标
完成一次“可追溯”的升级：升级前确认版本与备份，升级后验证运行，最后补全中文 changelog，并输出遗漏功能清单。

## 触发条件
- 升级 OpenClaw
- OpenClaw 更新
- 检查 OpenClaw 升级内容
- 生成 OpenClaw 更新日志

## 执行步骤
1. 先查当前版本（`openclaw --version`）
2. 查目标版本与通道（stable/beta/dev）
3. 拉取官方更新信息（CHANGELOG + Releases）
4. 升级前备份 `~/.openclaw/` 关键内容
5. 执行升级（`openclaw update` 或 npm/pnpm 更新）
6. 执行 `openclaw doctor`
7. 重启服务（pm2/systemd/launchd）
8. 验证服务与健康检查
9. 生成或更新中文 Markdown changelog
10. 输出“遗漏功能/配置”补充清单
11. 升级稳定后询问是否删除备份

## 补充清单检查项
- 新配置项是否需要写入
- 安全相关变更是否已启用
- 新插件/新模型是否需补充配置
- 通道与服务管理方式是否已对齐

## 输出格式
- 升级结果摘要（旧版本 → 新版本）
- changelog 文件路径
- 后续补充工作清单（Markdown）
- 备份文件路径与删除确认
