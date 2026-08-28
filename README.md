# 百炼 OCR for Bob

[![Verify](https://github.com/SchweppesSoda/bob-bailian-ocr/actions/workflows/verify.yml/badge.svg)](https://github.com/SchweppesSoda/bob-bailian-ocr/actions/workflows/verify.yml)

Bob 1.8+ 的阿里云百炼图片 OCR 插件，公开包使用按量付费接口。插件直接使用你在 Bob 设置中保存的 API Key 请求百炼，不经过第三方服务器。

## 安装

从 [最新 Release](https://github.com/SchweppesSoda/bob-bailian-ocr/releases/latest) 下载 `.bobplugin`，双击安装，然后在插件设置中填写对应计费模式的 API Key。

## 主要能力

- 支持 PNG、JPEG、WebP 和 GIF 图片输入，并自动识别 MIME。
- 使用 Bob 原生 `$data` 转换 Base64，结果按 Bob `texts` 逐行返回。
- 在 Base64 分配前检查图片大小，避免超大图片造成无效内存与上传开销。
- 默认模型为 `qwen3.7-plus`，按量付费可选择 `qwen3.5-ocr`。
- 提供 Auto、Fast、High 三档视觉分辨率；默认 Auto，小字图片可选 High。
- 思考默认关闭；通用视觉模型开启后可选择 Automatic、Low、Medium 或 High。
- 支持中国/新加坡按量付费、Workspace 地址和可信 HTTPS 自定义端点。
- 本地校验配置，不通过验证调用模型；API Key 错误信息自动脱敏。

插件固定非流式，不提供文字坐标或 Bounding Box。阿里云禁止 Coding Plan 与 Token Plan 用于自定义应用，因此公开 manifest 不提供这两条线路，运行时也会拒绝旧设置或手工传入的套餐模式。

## 验证状态

共享 Core、Bob 模拟宿主、macOS 合约 CI、图片格式、逐行结果和安装包结构均已自动测试。真实 Bob 应用内的安装与图片上传仍属于 Early Access 验证范围，欢迎在本仓库反馈结果。

## 源码关系

这是只负责 Bob 分发、appcast 和自动索引的薄仓库。权威源码位于 [`SchweppesSoda/manggo-bailian-plugin`](https://github.com/SchweppesSoda/manggo-bailian-plugin)，本版本由提交 [`73f50e3`](https://github.com/SchweppesSoda/manggo-bailian-plugin/commit/73f50e37e266c3318b04646cb8cd8b6068633dbc) 构建。

## License

[MIT](LICENSE)
