<!--
 * @Author: haoluo
 * @Date: 2019-07-23 19:57:12
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-24 09:31:31
 * @Description: file content
 -->

## VS Code 远程开发

**Visual Studio Code Remote Development** 允许您使用容器(container)、远程机器(remote machine)或用于 Linux 的 Windows 子系统(WSL)作为功能齐全的开发环境。您可以：

- 在您部署到或使用**更大或更专门的**硬件的**相同操作系统**上开发。
- **沙箱**您的开发环境，以避免影响您的**本地机器配置**。
- 让新的贡献者更容易**上手**，并让每个人都处于一个**一致的环境**中。
- 使用本地操作系统上**不可用**的工具或运行时，或管理它们的**多个版本**。
- 使用**用于 Linux 的 Windows 子系统**开发您的部署在 Linux 上的应用程序。
- 从**多台机器或位置**访问一个**现有**的开发环境。
- 调试**在其他地方运行的一个应用程序**，如一个客户站点或云中运行的应用程序。

要获得这些好处，在本地机器上**不需要源代码**。[远程开发扩展包](https://aka.ms/vscode-remote/download/extension) 中的每个扩展都可以直接在容器中、WSL 中或一个远程机器上运行命令和其他扩展，因此当您运行时，一切都感觉像在在本地运行一样。

![123](https://code.visualstudio.com/assets/docs/remote/remote-overview/architecture.png)

### 1. 开始

#### 1.1 远程开发扩展包

[远程开发扩展包](https://aka.ms/vscode-remote/download/extension) 包括三个扩展。阅读下面的文章来开始学习它们：

- [Remote - SSH](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/ssh.md) —— 使用 `SSH` 打开一个远程机器/VM 上的文件夹，连接到任何位置。
- [Remote - Containers](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/containers.md) —— 使用在容器内(或安装到)的沙箱工具链或基于容器的应用程序来工作。
- [Remote - WSL](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/wsl.md) —— 在 Linux 的 Windows 子系统中获得 Linux 支持的开发经验。

虽然大多数 VS Code 扩展应该在远程环境中不需要修改就可以工作，但是扩展作者可以在 [支持远程开发方面](https://code.visualstudio.com/api/advanced-topics/remote-extensions) 学到更多。

### 2. 问题或反馈

- 参见 [提示和技巧](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/tips_tricks.md) 或 [FAQ](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/faq.md)。
- 在 [Stack Overflow](https://stackoverflow.com/questions/tagged/vscode-remote) 上搜索。
- 添加一个 [特性请求](https://aka.ms/vscode-remote/feature-requests) 或 [报告一个问题](https://aka.ms/vscode-remote/issues/new)。
