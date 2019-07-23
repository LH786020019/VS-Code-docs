<!--
 * @Author: haoluo
 * @Date: 2019-07-23 09:06:45
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-23 15:35:33
 * @Description: file content
 -->

## 概述：设置 Visual Studio Code

使用 Visual Studio Code 启动和运行起来既快速又简单。这是一个小的下载，所以您可以在几分钟内安装并尝试 VS Code。

### 1. 跨平台

VS Code 是一个免费的代码编辑器，可以在 `macOS`、`Linux` 和 `Windows` 操作系统上运行。

遵循以下平台具体指南：

- [macOS](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/macos.md)
- [Linux](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/linux.md)
- [Windows](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/windows.md)

VS Code 是轻量级的，应该在大多数可用的硬件和平台版本上运行。您可以检查[系统需求](https://code.visualstudio.com/docs/supporting/requirements)，以检查是否支持您的计算机配置。

### 2. 更新频率

`VS Code` [每个月](https://code.visualstudio.com/updates)都会发布一个新版本，包含新特性和重要的 bug 修复。大多数平台都支持自动更新，当新版本可用时，系统会提示您安装新版本。您还可以通过运行 `Help > Check for Updates` 来手动检查更新。

> 注意：如果您喜欢按照自己的时间更新 VS Code ，可以[禁用自动更新](https://code.visualstudio.com/docs/supporting/faq#_how-do-i-opt-out-of-vs-code-autoupdates)。

### 3. 内部预览版构建

如果您想尝试我们的预览版构建，以便尽早看到新特性或验证 bug 修复，您可以安装我们的[内部构建](https://code.visualstudio.com/insiders)。内部构建与每月的稳定构建并行安装，您可以在同一台机器上自由地使用它们。内部构建与 VS Code 开发团队每天使用的构建是相同的，我们非常感谢人们尝试新特性并提供反馈。

### 4. 附加组件

VS Code 首先是一个编辑器，并且以占用空间小而自豪。与传统 IDEs 不同的是，传统 IDEs 倾向于包含除厨房水槽之外的所有东西，您可以根据您关心的开发技术调整您的安装。请务必在阅读平台指南之后阅读[附加组件](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/addi_comp.md)主题，以了解如何自定义 VS Code 安装。

### 5. 扩展

VS Code [扩展](https://love2.io/@LH786020019/doc/VS-Code-docs/user_guide/exten_market.md)允许第三方添加额外的支持：

- 语言 —— [C++](https://love2.io/@LH786020019/doc/VS-Code-docs/languages/cplusplus.md)、C#、Go、Java、Python
- 工具 —— ESLint、JSHint、PowerShell
- 调试器 —— Chrome、PHP XDebug。
- keymap —— Vim、Sublime Text、IntelliJ、Emacs、Atom、Visual Studio、Eclipse

扩展集成到 VS Code 的 UI、命令和任务运行系统中，因此您会发现通过 VS Code 的共享接口可以轻松地使用不同的技术。查看 VS Code 扩展 [Marketplace](https://marketplace.visualstudio.com/vscode)，看看有什么可用。

### 6. 下一个步骤

一旦你安装和设置 VS Code ，这些主题将帮助你了解关于 VS Code 的更多信息：

- [额外组件](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/addi_comp.md) —— 学习如何安装 `Git`、`Node.js`、`TypeScript` 和类似 `Yeoman` 的工具。
- [用户界面](https://love2.io/@LH786020019/doc/VS-Code-docs/get_started/user_interface.md) —— VS Code 的快速定位。
- [基本编辑](https://love2.io/@LH786020019/doc/VS-Code-docs/user_guide/basic_editing.md) —— 了解功能强大的 VS Code 编辑器。
- [代码导航](https://love2.io/@LH786020019/doc/VS-Code-docs/user_guide/code_navi.md) —— 快速浏览源代码。
- [调试](https://love2.io/@LH786020019/doc/VS-Code-docs/user_guide/debugging.md) —— 在 VS Code 编辑器中直接调试源代码。
- [代理服务器支持](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/network.md) —— 配置您的代理设置。

如果您想快速运行一些东西，请尝试 [Node.js 教程](https://code.visualstudio.com/docs/nodejs/nodejs-tutorial)演练，这将让您在几分钟内用 VS Code 调试 Node.js web 应用程序。

### 7. 常见问题

#### 7.1 VS Code 的系统需求是什么?

我们有一个[系统需求](https://code.visualstudio.com/docs/supporting/requirements)列表。

#### 7.2 VS Code 有多大?

VS Code 是一个很小的下载(< 100 MB)，磁盘占用空间小于 200 MB，因此您可以快速安装 VS Code 并试用它。

#### 7.3 我如何创建和运行一个新项目?

VS Code 不包括一个传统的 `File > New Project` 对话框或预安装的项目模板。您需要根据您的开发兴趣添加[额外的组件](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/addi_comp.md)和脚手架(scaffolders)。使用脚手架工具(如 [Yeoman](http://yeoman.io/))和 [npm](https://www.npmjs.com/) 包管理器提供的大量模块，您肯定可以找到合适的模板和工具来创建项目。

#### 7.4 我如何知道我在运行哪个版本?

在 Linux 和 Windows 上，选择 `Help > About`。在 macOS 上，使用 `Code > About Visual Studio Code`。

#### 7.5 为什么 VS Code 说我的安装不受支持?

VS Code 检测到一些安装文件被修改，很可能是通过一个扩展。重新安装 VS Code 将替换受影响的文件。更多细节请参见我们的 [FAQ](https://code.visualstudio.com/docs/supporting/faq#_installation-appears-to-be-corrupt-unsupported) 主题。
