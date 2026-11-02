# Atria-ZD（宅董风格桌面 6×6 定制版 · 远程构建）

编译时自动拉取 [s-gdn/Atria-iOS17](https://github.com/s-gdn/Atria-iOS17)（GPL-3.0）源码并应用本仓库 `patches/` 中的补丁。

## 补丁内容

1. `patches/Makefile`：包方案改为 `?=`，同一份源码可编译 rootless / roothide 两种 deb
2. `patches/me.lau.AtriaPrefs.plist`：预置默认布局——**桌面 6 列 × 6 行、图标缩放 0.85、显示标签、Dock 5 列、关闭欢迎弹窗**，安装后即生效
3. CI 同时产出 rootless 与 roothide 包

## 使用

- **Relaxin（RootHide）越狱装 `Atria-ZD.roothide.deb`**；Dopamine 等 rootless 越狱装 `.rootless.deb`
- Filza 打开 deb → Install → 注销
- 桌面长按进入 Atria 编辑模式，可微调行列、图标大小、间距、每个图标的位置
- 恢复默认：删除 `/var/mobile/Library/Preferences/me.lau.AtriaPrefs.plist` 后注销

## 注意

- 上游仅在 iOS 17.1.1–17.3.1 验证过，17.0 未经真机确认；弹安全模式请卸载并反馈
- iOS 18+ 不支持（上游限制）
- 若编译报缺 `libcolorpicker`，在 workflow 的构建步骤里去掉 `SUBPROJECTS += Prefs`（通过修改 patches/Makefile）即可只损失设置面板
