# ETF 量化看板

适用于 Apple Silicon Mac（M1 / M2 / M3 / M4 等），需要 macOS 13 或以上。

[下载 DMG 安装包](https://github.com/laolee9/ETF/releases/latest)

## 安装与使用

1. 下载 Release 中的 `ETFQuantDashboard-1.0.1-AppleSilicon.dmg`。
2. 双击打开，将「ETF量化看板」拖到「Applications」。
3. 从「应用程序」打开。首次启动会恢复内置行情数据库，稍候即可使用。

已内置运行环境、ETF 清单和行情快照，无需安装 Python。查看已有行情可离线使用；更新行情需要网络。升级时替换应用即可，已有用户数据会保留。

菜单「数据 → 打开数据文件夹」可查看或管理数据库与清单；「数据 → 查看运行日志」用于排查运行问题。应用退出时会停止本地服务。

## 首次打开

当前版本采用本地代码签名，尚未进行 Apple 开发者公证。若系统提示无法验证开发者，可按 [Apple 官方说明](https://support.apple.com/zh-cn/102445)，在「系统设置 → 隐私与安全性」中允许打开。

## 版本校验

Release 附有 `.sha256` 校验文件，用于检查下载完整性。此仓库提供 macOS 安装包及使用说明。
