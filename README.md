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

当前版本采用本地代码签名，尚未进行 Apple 开发者公证。macOS 可能因下载隔离标记（`com.apple.quarantine`）阻止启动。

先按 [Apple 官方说明](https://support.apple.com/zh-cn/102445) 操作：

1. 将应用拖到「Applications」，从「应用程序」尝试打开一次。
2. 打开「系统设置 → 隐私与安全性」，点击「仍要打开」。
3. 如果再次出现确认提示，点击「打开」，按系统要求完成验证。

### 点击「仍要打开」后仍无反应

如果图标跳动后消失，或进程存在但没有窗口，下载隔离检查仍可能阻止程序加载。该症状也可能有其他原因；以下步骤用于处理隔离标记问题。

仅在确认安装包来自本仓库 Release、完成版本校验并愿意运行这个未经公证的应用后，打开「终端」执行：

```bash
xattr -dr com.apple.quarantine "/Applications/ETF量化看板.app"
open "/Applications/ETF量化看板.app"
```

这会持久移除该应用及其内部文件的下载隔离标记，范围仅为上述应用路径。如果后台已有无响应的「ETF量化看板」进程，先通过「活动监视器」退出该进程，再重新打开应用。

首次正常启动会恢复内置数据库，请稍候。若仍打不开，可检查运行日志：

```text
~/Library/Application Support/ETFQuantDashboard/app.log
```

用户数据也保存在上述目录，无需为解决启动问题删除它。

### 关于后续下载

隔离标记由下载者的 macOS 添加，本机清除后重新上传 DMG，无法保证其他人下载时不再出现。以上方法是当前未公证版本的本地处理方法。要从发布流程解决此问题，需要使用 Developer ID 签名、Apple 公证并附加公证票据；相关流程见 [Apple 开发者文档](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution)。

## 版本校验

Release 附有 `.sha256` 校验文件，用于检查下载完整性。将 DMG 和对应的校验文件下载到同一文件夹后，在终端执行：

```bash
cd "$HOME/Downloads"
shasum -a 256 -c ETFQuantDashboard-1.0.1-AppleSilicon.dmg.sha256
```

确认输出为 `ETFQuantDashboard-1.0.1-AppleSilicon.dmg: OK`。校验值一致表示文件与发布包相符，不等于通过 Apple 公证。此仓库提供 macOS 安装包及使用说明。
