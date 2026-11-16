# 平桌面 · PingLauncher

面向 Android 的轻量桌面启动器。所有应用平铺在桌面，不使用应用抽屉。

当前版本 **3.12**，包名 `wang.lucian.pinglauncher`，最低 Android 8.0，compile/target SDK 35。设计面向 Android 17 使用场景，Android 17 真机兼容性仍需持续验证。


## 正式版下载与构建

打开 [Signed Android release](https://github.com/Lucian-Wang/PingLauncher/actions/workflows/android-release.yml)，选择成功的运行，在 Artifacts 下载 `PingLauncher-signed-release`，内含正式签名 APK 和 SHA256SUMS.txt。已发布标签的安装包见 [Releases](https://github.com/Lucian-Wang/PingLauncher/releases)。

`main` 提交和手动运行会生成构建产物；推送 `v*` 标签后发布 Release。手动构建支持 `version_name`、`version_code`，配置说明见 [RELEASE.md](RELEASE.md)。当前流程使用 Lucian 签名并核验 APK 包名、证书指纹和非调试属性。相同包名但签名不同的 APK 不能覆盖安装。

## 功能

- 稀疏网格：图标可移动到空格，保留空位；支持自定义排序与跨屏拖动。
- 新安装应用紧接桌面最后一个可见图标，不回填首页空位。
- 网格与 Dock 按可用空间适配；支持桌面与 Dock 之间移动，Dock 图标不在桌面重复显示。
- 图标长按快捷菜单、应用快捷操作、应用信息与卸载入口。
- 独立设置页面；隐藏应用、密码入口与隐藏应用列表。
- 可选通知红点；通过无障碍服务支持桌面下滑展开通知栏。

通知红点需要用户主动授予通知使用权；下滑通知栏需要用户主动启用无障碍服务。系统或设备厂商可能限制应用快捷操作、卸载与系统面板行为。

## 构建

安装 JDK 17、Android SDK Platform 35 与 Build Tools 35.0.0。设置 `ANDROID_HOME`，或在未提交的 `local.properties` 中填写 `sdk.dir`。

```powershell
.\gradlew.bat :app:assembleDebug :app:lintDebug
```

Linux/macOS：`chmod +x gradlew && ./gradlew :app:assembleDebug :app:lintDebug`。

APK 输出到 `app/build/outputs/apk/debug/`。源码仓库不包含原开发签名；自行构建的 APK 通常不能直接覆盖此前分享的安装包。不要提交签名文件或口令。

`tests/` 保留现有网格、分页、Dock 与设备验证源码；构建命令不运行这些独立验证程序。

## 数据与限制

桌面布局、隐藏应用配置和密码校验数据保存在本机；本项目未集成广告、统计或远程账号服务。隐藏应用仅隐藏本启动器中的入口，系统设置或其他启动器仍可发现应用。详见 [隐私说明](PRIVACY.md)。

目前未提供文件夹、桌面小部件或云端同步。不同设备上的触控、系统通知栏及 Android 17 行为需要真机验证。

## 许可证

采用 [Apache License 2.0](LICENSE)。与静话分别维护：[QuietCalls](https://github.com/Lucian-Wang/QuietCalls)。


## 应用标识

应用 ID：`wang.lucian.pinglauncher`。本次包名变更后的 APK 会作为独立应用安装，不能覆盖升级旧包名版本；旧应用的数据和授权不会自动迁移，请先导出需要保留的数据，再安装并重新授权。

## 维护与反馈

维护者：[Lucian](https://lucian.wang/) · 邮箱：im@lucian.wang · [问题反馈](https://github.com/Lucian-Wang/PingLauncher/issues)
