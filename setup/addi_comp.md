<!--
 * @Author: haoluo
 * @Date: 2019-07-23 09:06:14
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-23 17:50:54
 * @Description: file content
 -->

- [附加组件和工具](#%e9%99%84%e5%8a%a0%e7%bb%84%e4%bb%b6%e5%92%8c%e5%b7%a5%e5%85%b7)
  - [1. 常用的组件](#1-%e5%b8%b8%e7%94%a8%e7%9a%84%e7%bb%84%e4%bb%b6)
  - [2. VS Code 扩展](#2-vs-code-%e6%89%a9%e5%b1%95)
  - [3. 附加工具](#3-%e9%99%84%e5%8a%a0%e5%b7%a5%e5%85%b7)
  - [4. 下一步](#4-%e4%b8%8b%e4%b8%80%e6%ad%a5)

## 附加组件和工具

Visual Studio Code 是按设计进行的少量下载，只包含在大多数开发工作流中共享的最少组件数量。包括编辑器、文件管理、窗口管理和首选项设置等基本功能。`JavaScript/TypeScript` 语言服务和 `Node.js` 调试器也是基本安装的一部分。

如果您习惯于使用更大的、统一的开发工具(IDEs)，您可能会惊讶地发现，您的场景并没有完全得到开箱即用的支持。例如，没有带有预安装项目模板的 `File > New Project` 对话框。大多数 VS Code 用户将需要根据他们的特定需要安装额外的组件。

### 1. 常用的组件

以下是一些常见的安装组件：

- [Git](https://git-scm.com/download) —— VS Code 内置了对使用 Git 进行源代码控制的支持，但是需要单独安装 Git。
- [Node.js(包括npm)](https://nodejs.org/) —— 一个跨平台运行时，用于构建和运行 JavaScript 应用程序。
- [TypeScript](https://www.typescriptlang.org/) —— TypeScript 编译器，`tsc`，用于将 TypeScript 转换为 JavaScript。

您将在我们的文档和演练中经常发现上述组件。

### 2. VS Code 扩展

您可以通过[扩展](https://love2.io/@LH786020019/doc/VS-Code-docs/user_guide/exten_market.md)来扩展 VS Code 编辑器本身。VS Code 社区已经在 VS Code [Marketplace](https://marketplace.visualstudio.com/VSCode)上构建了数百个有用的扩展。

- [python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) —— Linting、调试(多线程、远程)、智能感知、代码格式化、重构、单元测试、代码片段等等。
- [C/C++](https://love2.io/@LH786020019/doc/VS-Code-docs/languages/cplusplus.md) —— C/C++ 智能感知、调试和代码浏览。
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) —— 将 `ESLint JavaScript` 集成到 VS Code 中。
- [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome) —— 在 Chrome 浏览器或任何其他支持 `Chrome Debugger` 协议的目标中调试 `JavaScript` 代码。
- [vscode-icons](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons) —— 用于 VS Code 的图标
- [Language Support for Java(TM) by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.java) —— Java Linting、智能感知、格式化、重构、Maven/Gradle支持等等。
- [GitLens — Git supercharged](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) —— 增强 Visual Studio Code 内置的 `Git` 功能 —— 通过 `Git blame` 注释和 `Code lens` 查看代码作者，无缝导航和探索 Git 存储库，通过强大的比较命令获得有价值的见解，等等
- [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur) —— 用于 VS Code 的 `Vue` 工具

上面显示的扩展是目前市场上最流行的。单击上面的扩展块来阅读扩展的描述和评论。

### 3. 附加工具

Visual Studio Code 与现有的工具链集成。我们认为以下工具将增强您的开发经验。

- [Yeoman](http://yeoman.io/) —— 一个应用程序脚手架工具，命令行版本的 `File > New Project`。
- [generator-aspnet](https://www.npmjs.com/package/generator-aspnet) —— 一个用于 scaffold [ASP.NET Core](https://asp.net/) 应用程序的 Yeoman 生成器。
- [generator-hottowel](https://github.com/johnpapa/generator-hottowel) —— 一个用于快速创建 AngularJS 应用程序的 Yeoman 生成器。
- [Express](https://expressjs.com/) —— 一个使用 Jade 模板引擎的用于 Node.js 应用程序的应用程序框架。
- [Gulp](https://gulpjs.com/) —— 一个流任务运行器系统，可以很容易地与 VS Code 任务集成。
- [Mocha](https://mochajs.org/) —— 一个运行在 Node.js 上的 JavaScript 测试框架。
- [Yarn](https://yarnpkg.com/) —— 一个依赖管理器和替代 npm。

> 注意：大多数这些工具都需要 Node.js 和 npm 包管理器来安装和使用。

### 4. 下一步

- [用户界面](https://love2.io/@LH786020019/doc/VS-Code-docs/get_started/user_interface.md) —— 围绕 VS Code 的快速定位。
- [用户/工作区设置](https://love2.io/@LH786020019/doc/VS-Code-docs/get_started/settings.md) —— 学习如何通过 settings 配置 VS Code 到您的首选项。
- [语言](https://love2.io/@LH786020019/doc/VS-Code-docs/languages/overview.md) —— VS Code 支持许多开箱即用的编程语言，以及通过社区创建的扩展支持更多的编程语言。
