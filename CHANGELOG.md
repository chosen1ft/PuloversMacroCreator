# 更新日志 / Changelog

基于 Pulover's Macro Creator **v5.4.1** 的定制修改说明。

---

## [定制版] — 2026-08-13

### 界面与功能精简

- **仅保留英文界面**：移除多语言选择、语言编辑器、翻译提交相关逻辑与界面。
- **取消语言文件运行时加载**：英文文案内嵌至 `LIB\Lang_en.ahk`，启动不再读取 `Lang\*.lang`；安装包/便携版也不再附带 Lang 目录。
- **移除首次启动欢迎页**：不再显示语言与布局选择界面。
- **移除启动 Tips 对话框**：取消首次启动提示，以及帮助菜单中的 Tips 入口。
- **仅使用 Default 工具栏布局**：移除 Basic / Best Fit 等布局选项与布局菜单；启动始终使用默认工具栏布局。
- **移除预览与语法高亮**：删除 Scintilla 预览窗口及相关依赖（保留导出与脚本编辑相关能力）。
- **移除应用级联网功能**：取消自动更新、在线帮助链接、捐赠菜单、语言包/OCR 数据在线下载等（宏命令内的网络能力如下载、邮件等仍保留）。
- **移除小图标模式**：工具栏固定使用大图标（24×24）。

### 问题修复

- 修复粘贴/删除条目后误弹出 “Move here / Copy here / Cancel” 菜单（子程序缺少 `return` 导致穿透到拖放菜单）。
- 修复关于对话框点击 OK 后主窗口被压到 Z 序底层不显示的问题。
- 修复设置窗口因缺失 `SearchFile` 标签导致打开报错。
- 修复语言编辑器残留热键调用已删除标签 `GoNextLine` / `GoPrevLine` 导致启动报错。
- 修复版权符号 ©、颜色色块 █ 等 Unicode 显示乱码（脚本改为 UTF-8 BOM）。
- 修复内嵌语言文件导致 Ahk2Exe 编译失败（超长字符串拆分拼接，兼容编译器限制）。

### 构建与分发

- `Compile.ahk`、`Installer.iss`、`BuildFiles.ahk`：不再复制/安装语言包与中文帮助 CHM。
- 帮助仅打开 `MacroCreator_Help.chm`。
- 保留 `Lang\en.lang` 与 `_embed_lang.ps1`，仅作为重新生成内嵌文案的源文件（运行时不依赖）。

### 说明

- 若仍使用旧版 `%AppData%\MacroCreator\MacroCreator.ini`，其中已废弃的键（如 `ShowTips`、`UserLayout`、`Lang` 等）会被忽略，下次保存设置时不再写入。
- 修改 `Lang\en.lang` 后需运行 `_embed_lang.ps1` 重新生成 `LIB\Lang_en.ahk`，再编译。
