# Changelog

## [1.0.0] - 2026-11-17

首个完整版本：把分页列表页转成干净 CSV，**零第三方依赖**。

### Added

- 仅用 `urllib` + `html.parser` 实现，无需 `pip install`，复制即运行
- 轻量 DOM 树与 CSS 选择器子集：`tag`、`.class`、`#id`、`[attr=value]`、后代组合器
- 字段映射配置：一个字段可组合多个选择器与属性（如 `a[href]@href`）
- 分页抓取，支持 `{page}` 占位符与最大页数保护
- 失败重试（指数退避）与请求间隔限速，避免给目标站点造成压力
- CSV 输出带 UTF-8 BOM，Excel 直接打开不乱码
- 26 项单元测试（无网络依赖，用本地 HTML 片段与 `demo.html` 验证）
- GitHub Actions CI：Python 3.9 / 3.11 / 3.13

### Changed

- 移除了误提交的 `__pycache__/` 编译产物，改为 `.gitignore` 忽略

### Notes

- 已知限制：选择器不支持伪类与 `nth-child`；不执行 JavaScript，动态渲染页面需另配数据接口
- 合规提示：使用时请遵守目标站点的 `robots.txt` 与服务条款，本工具默认低频率抓取
