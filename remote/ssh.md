<!--
 * @Author: haoluo
 * @Date: 2019-07-23 20:20:08
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-24 09:32:13
 * @Description: file content
 -->

- [使用 SSH 进行远程开发](#%e4%bd%bf%e7%94%a8-ssh-%e8%bf%9b%e8%a1%8c%e8%bf%9c%e7%a8%8b%e5%bc%80%e5%8f%91)
  - [1. 开始](#1-%e5%bc%80%e5%a7%8b)
    - [1.1 系统需求](#11-%e7%b3%bb%e7%bb%9f%e9%9c%80%e6%b1%82)
    - [1.2 安装](#12-%e5%ae%89%e8%a3%85)
    - [1.3 连接到一个远程主机](#13-%e8%bf%9e%e6%8e%a5%e5%88%b0%e4%b8%80%e4%b8%aa%e8%bf%9c%e7%a8%8b%e4%b8%bb%e6%9c%ba)
    - [1.4 记住你经常连接的主机](#14-%e8%ae%b0%e4%bd%8f%e4%bd%a0%e7%bb%8f%e5%b8%b8%e8%bf%9e%e6%8e%a5%e7%9a%84%e4%b8%bb%e6%9c%ba)
  - [2. 管理扩展](#2-%e7%ae%a1%e7%90%86%e6%89%a9%e5%b1%95)
    - [2.1 "Always installed" 扩展](#21-%22always-installed%22-%e6%89%a9%e5%b1%95)
    - [2.2 高级：强制一个扩展在本地/远程运行](#22-%e9%ab%98%e7%ba%a7%e5%bc%ba%e5%88%b6%e4%b8%80%e4%b8%aa%e6%89%a9%e5%b1%95%e5%9c%a8%e6%9c%ac%e5%9c%b0%e8%bf%9c%e7%a8%8b%e8%bf%90%e8%a1%8c)
  - [3. 转发一个端口 / 创建 SSH tunnel](#3-%e8%bd%ac%e5%8f%91%e4%b8%80%e4%b8%aa%e7%ab%af%e5%8f%a3--%e5%88%9b%e5%bb%ba-ssh-tunnel)
    - [3.1 临时转发一个端口](#31-%e4%b8%b4%e6%97%b6%e8%bd%ac%e5%8f%91%e4%b8%80%e4%b8%aa%e7%ab%af%e5%8f%a3)
    - [3.2 总是转发一个端口](#32-%e6%80%bb%e6%98%af%e8%bd%ac%e5%8f%91%e4%b8%80%e4%b8%aa%e7%ab%af%e5%8f%a3)
  - [4. 打开远程主机上的终端](#4-%e6%89%93%e5%bc%80%e8%bf%9c%e7%a8%8b%e4%b8%bb%e6%9c%ba%e4%b8%8a%e7%9a%84%e7%bb%88%e7%ab%af)
  - [5. 在 SSH 主机上调试](#5-%e5%9c%a8-ssh-%e4%b8%bb%e6%9c%ba%e4%b8%8a%e8%b0%83%e8%af%95)
  - [6. SSH 主机特定的设置](#6-ssh-%e4%b8%bb%e6%9c%ba%e7%89%b9%e5%ae%9a%e7%9a%84%e8%ae%be%e7%bd%ae)
  - [7. 使用本地工具工作](#7-%e4%bd%bf%e7%94%a8%e6%9c%ac%e5%9c%b0%e5%b7%a5%e5%85%b7%e5%b7%a5%e4%bd%9c)
  - [8. 已知的限制](#8-%e5%b7%b2%e7%9f%a5%e7%9a%84%e9%99%90%e5%88%b6)
    - [8.1 Remote - SSH 限制](#81-remote---ssh-%e9%99%90%e5%88%b6)
    - [8.2 Docker 扩展限制](#82-docker-%e6%89%a9%e5%b1%95%e9%99%90%e5%88%b6)
    - [8.3 扩展限制](#83-%e6%89%a9%e5%b1%95%e9%99%90%e5%88%b6)
  - [9. 常见问题](#9-%e5%b8%b8%e8%a7%81%e9%97%ae%e9%a2%98)
    - [9.1 如何在 XXX 上设置 SSH client？](#91-%e5%a6%82%e4%bd%95%e5%9c%a8-xxx-%e4%b8%8a%e8%ae%be%e7%bd%ae-ssh-client)
    - [9.2 如何在 XXX 上设置 SSH server？](#92-%e5%a6%82%e4%bd%95%e5%9c%a8-xxx-%e4%b8%8a%e8%ae%be%e7%bd%ae-ssh-server)
    - [9.3 我可以使用其他/额外的身份验证机制(比如密码)登录 SSH 服务器吗？](#93-%e6%88%91%e5%8f%af%e4%bb%a5%e4%bd%bf%e7%94%a8%e5%85%b6%e4%bb%96%e9%a2%9d%e5%a4%96%e7%9a%84%e8%ba%ab%e4%bb%bd%e9%aa%8c%e8%af%81%e6%9c%ba%e5%88%b6%e6%af%94%e5%a6%82%e5%af%86%e7%a0%81%e7%99%bb%e5%bd%95-ssh-%e6%9c%8d%e5%8a%a1%e5%99%a8%e5%90%97)
    - [9.4 如何修复关于 "bad permissions" 的 SSH 错误？](#94-%e5%a6%82%e4%bd%95%e4%bf%ae%e5%a4%8d%e5%85%b3%e4%ba%8e-%22bad-permissions%22-%e7%9a%84-ssh-%e9%94%99%e8%af%af)
    - [9.5 需要在远程 SSH 主机上安装哪些 Linux 包/库？](#95-%e9%9c%80%e8%a6%81%e5%9c%a8%e8%bf%9c%e7%a8%8b-ssh-%e4%b8%bb%e6%9c%ba%e4%b8%8a%e5%ae%89%e8%a3%85%e5%93%aa%e4%ba%9b-linux-%e5%8c%85%e5%ba%93)
    - [9.6 当 VS Code Server 运行在一个 远程机器 / VM 上时，它的连接性要求是什么？](#96-%e5%bd%93-vs-code-server-%e8%bf%90%e8%a1%8c%e5%9c%a8%e4%b8%80%e4%b8%aa-%e8%bf%9c%e7%a8%8b%e6%9c%ba%e5%99%a8--vm-%e4%b8%8a%e6%97%b6%e5%ae%83%e7%9a%84%e8%bf%9e%e6%8e%a5%e6%80%a7%e8%a6%81%e6%b1%82%e6%98%af%e4%bb%80%e4%b9%88)
    - [9.7 我可以在远程 SSH 主机上的源代码上使用本地工具吗？](#97-%e6%88%91%e5%8f%af%e4%bb%a5%e5%9c%a8%e8%bf%9c%e7%a8%8b-ssh-%e4%b8%bb%e6%9c%ba%e4%b8%8a%e7%9a%84%e6%ba%90%e4%bb%a3%e7%a0%81%e4%b8%8a%e4%bd%bf%e7%94%a8%e6%9c%ac%e5%9c%b0%e5%b7%a5%e5%85%b7%e5%90%97)
    - [9.8 当我只有 SFTP/FTP 文件系统访问我的远程主机(没有 shell 访问)时，我可以使用 VS Code 吗？](#98-%e5%bd%93%e6%88%91%e5%8f%aa%e6%9c%89-sftpftp-%e6%96%87%e4%bb%b6%e7%b3%bb%e7%bb%9f%e8%ae%bf%e9%97%ae%e6%88%91%e7%9a%84%e8%bf%9c%e7%a8%8b%e4%b8%bb%e6%9c%ba%e6%b2%a1%e6%9c%89-shell-%e8%ae%bf%e9%97%ae%e6%97%b6%e6%88%91%e5%8f%af%e4%bb%a5%e4%bd%bf%e7%94%a8-vs-code-%e5%90%97)
    - [9.9 作为一个扩展作者，我需要做什么？](#99-%e4%bd%9c%e4%b8%ba%e4%b8%80%e4%b8%aa%e6%89%a9%e5%b1%95%e4%bd%9c%e8%80%85%e6%88%91%e9%9c%80%e8%a6%81%e5%81%9a%e4%bb%80%e4%b9%88)
    - [9.10 问题或反馈](#910-%e9%97%ae%e9%a2%98%e6%88%96%e5%8f%8d%e9%a6%88)

## 使用 SSH 进行远程开发

**Visual Studio Code Remote - SSH** 扩展允许您打开一个远程文件夹，它可位于任何远程机器上、虚拟机、或运行 SSH 服务器的容器上和充分利用 VS Code 的特性集，一旦连接到一个服务器，您可以与远程文件系统上的任何文件和文件夹交互。

由于此扩展直接在远程机器上运行命令和其他扩展，因此不需要在本地机器上运行源代码就可以获得这些好处。

![ssh](https://code.visualstudio.com/assets/docs/remote/ssh/architecture-ssh.png)

这使得 VS Code 提供了一个**本地质量的开发体验** —— 包括完整的智能感知(补全)、代码导航和调试 —— **无论您的代码位于何处**。

### 1. 开始

#### 1.1 系统需求

**本地**：参见 [VS Code](https://code.visualstudio.com/docs/supporting/requirements) 的最低要求。还必须安装支持 [OpenSSH 兼容的 SSH Client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client)。

**远程 SSH 主机**：正在以下平台上运行的一个 [SSH Server](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-server)：

- **完全支持**：x86_64 Debian 8+、Ubuntu 16.04+、CentOS / RHEL 7+。
- **实验支持**：ARMv7l Raspbian 8+(32位) 只在 [Visual Studio Code Insiders](https://code.visualstudio.com/insiders/) 上。

如果具备必要的先决条件，其他基于 `glibc` 的用于 x86_64 和 ARMv7l 的 Linux 发行版(在 VS Code Insiders 中)应该可以工作。有关启动和运行社区支持的发行版的信息先决条件和技巧，请参阅 [使用 Linux 进行远程开发](https://code.visualstudio.com/docs/remote/linux) 的文章。

虽然实验性的 ARMv7l 支持在 [VS Code Insiders](https://code.visualstudio.com/insiders/) 是可用的，但是安装在 ARMv7l 设备上的一些扩展可能无法工作，因为在扩展中使用了 x86 本地代码。

#### 1.2 安装

首先，您需要：

1. 如果还没有 [OpenSSH 兼容的 SSH Client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client)，则安装它。
2. 安装 [Visual Studio Code](https://code.visualstudio.com/) 或 [Visual Studio Code Insiders](https://code.visualstudio.com/insiders/)。
3. 安装 [远程开发扩展包](https://aka.ms/vscode-remote/download/extension)。
4. [可选]如果您在 macOS 或 Linux 上，需要在连接到主机时输入令牌或密码，可以 [在 SSH 配置中启用 `ControlMaster`](https://code.visualstudio.com/docs/remote/troubleshooting#_enabling-alternate-ssh-authentication-methods)，以避免多次输入令牌或密码。

#### 1.3 连接到一个远程主机

Visual Studio Code 使用 [SSH 配置文件](https://linux.die.net/man/5/ssh_config)，需要[基于 SSH 密钥的身份验证](https://www.ssh.com/ssh/public-key-authentication)才能连接到您的主机。如果您还没有一个主机，可以 [在 Azure 上创建一个 Linux VM](https://docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)，或者 [在现有机器上设置一个 SSH 主机](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-server)。

> 注意：有关受支持的 SSH 主机的信息，请参阅 [系统需求](https://code.visualstudio.com/docs/remote/ssh#_system-requirements)。当在 [Visual Studio Code Insiders](https://code.visualstudio.com/insiders/) 中使用对 ARMv7l `glibc` 发行版(如Raspbian)的实验性支持时，请注意，安装在远程主机上的一些扩展可能无法工作，因为在扩展中使用了 x86 本地代码。

要开始，请遵循以下步骤：

1. 首先，通过在计划连接的主机上将本地公共 SSH 密钥添加到 `~/.ssh/authorized_keys`，在此主机上**配置基于密钥的身份验证**。如果您是 SSH 新手或者遇到了麻烦，请参阅 [配置基于密钥的身份验证](https://code.visualstudio.com/docs/remote/troubleshooting#_configuring-key-based-authentication)，以获得关于设置此身份验证的更多信息。如果您遵循  Azure VM 教程，您可以跳过这一步。
    > 注意：如果跳过此步骤，由于 [vscode-remote-release#642](https://github.com/microsoft/vscode-remote-release/issues/642)，您将需要输入两次密码。还要注意，用于 Windows 的 PuTTY 不是一个 [受支持的客户端](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client)，但是您可以 [转换您的 PuTTYGen keys](https://code.visualstudio.com/docs/remote/troubleshooting#_reusing-a-key-generated-in-puttygen)。
2. 从命令面板(`F1`)中运行 `Remote-SSH: Connect to Host...`，在输入框中输入主机和此主机上的用户，如下所示：`user@hostname`。
    ![host](https://code.visualstudio.com/assets/docs/remote/ssh/ssh-user@box.png)
    > 注意:如果您在连接时看到有关 SSH 文件权限错误的信息，请参阅 [修复 SSH 文件权限错误](https://code.visualstudio.com/docs/remote/troubleshooting#_fixing-ssh-file-permission-errors) 以了解正确设置的详细信息。
3. 过一会儿，VS Code 将连接到 SSH 服务器并设置它自己。VS Code 将使用一个进度通知使您保持最新状态，您可以在 `Remote - SSH` 输出通道中看到详细的日志。
    > 注意：如果连接挂起，可能需要启用 TCP 转发或响应一个服务器提示。有关详细信息，请参阅 [提示和技巧](https://code.visualstudio.com/docs/remote/troubleshooting#_troubleshooting-hanging-or-failing-connections)。
4. 连接好后，您将处于一个空窗口中。然后，您可以使用 `File > Open...` 或 `File > Open Workspace...` 在远程机器上打开一个文件夹或工作区。
5. 过一会儿，您选择的文件夹或工作区将打开。从 Extensions 视图中安装要在此主机上使用的任何扩展。

#### 1.4 记住你经常连接的主机

如果有一些经常使用的主机，可以将它们添加到一个 SSH 配置文件中，这样它们就会自动出现在主机下拉列表中。运行 `Remote-SSH: Open Configuration File...` 并使用 [SSH 配置文件格式](https://linux.die.net/man/5/ssh_config) 将主机添加到文件中。

例如，这里有两个示例主机：

```txt
Host example-remote-linux-machine
    User your-user-name-here
    HostName host-fqdn-or-ip-goes-here

Host example-remote-linux-machine-with-identity-file
    User your-user-name-on-host
    HostName another-host-fqdn-or-ip-goes-here
    IdentityFile ~/.ssh/id_rsa-remote-ssh
```

如果希望使用多个 SSH 密钥，则第二个示例为 SSH 密钥使用一个备用位置。有关详细信息，请参阅 [提示和技巧](https://code.visualstudio.com/docs/remote/troubleshooting#_improving-your-security-with-a-dedicated-key)。如果您想使用与列出的配置文件不同的配置文件，您还可以在 `settings.json` 中设置 `"remote.SSH.configFile"` 属性。

### 2. 管理扩展

VS Code 在以下两个地方之一运行扩展：本地的 UI /client 端，或者远程的 SSH 主机。虽然影响 VS Code UI 的扩展(比如主题和代码片段)是在本地安装的，但是大多数扩展将驻留在 SSH 主机上。这可以确保您拥有流畅的体验，并允许您从本地机器上为 SSH 主机上的给定工作区安装所需的任何扩展。通过这种方式，您可以准确地从您停止的地方继续，从带有您的扩展的一个不同机器完成。

如果您从 Extensions 视图中安装一个扩展，它将自动安装在正确的位置。安装后，您可以根据类别分组确定扩展安装在何处。这里将有一个用于您的远程 SSH 主机的类别和一个 `Local - Installed` 类别。
![ssh](https://code.visualstudio.com/assets/docs/remote/ssh/ssh-installed-remote-indicator.png)
![local](https://code.visualstudio.com/assets/docs/remote/common/local-installed-extensions.png)
> 注意：如果您是一个扩展作者，并且发现您的扩展不能正常工作或安装在错误的位置，请参阅 [支持远程开发](https://code.visualstudio.com/api/advanced-topics/remote-extensions) 以获得详细信息。

实际上需要远程运行的本地扩展将在 `Local - Installed` 类别中 `Disabled`。选择 `Install` 以在远程主机上安装一个扩展。
![live server](https://code.visualstudio.com/assets/docs/remote/ssh/ssh-disabled-extensions.png)

#### 2.1 "Always installed" 扩展

如果希望始终在任何 SSH 主机上安装扩展，可以使用 `settings.json` 中的 `remote.SSH.defaultExtensions` 属性指定哪些扩展。例如，如果您想安装 [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) 和 [Resource Monitor](https://marketplace.visualstudio.com/items?itemName=mutantdino.resourcemonitor) 扩展，请指定它们的扩展 IDs 如下：

```json
"remote.SSH.defaultExtensions": [
    "eamodio.gitlens",
    "mutantdino.resourcemonitor"
]
```

#### 2.2 高级：强制一个扩展在本地/远程运行

扩展通常设计并测试为本地或远程运行，而不是同时运行。但是，如果扩展支持它，则可以在 `settings.json` 文件中设置强制它在特定位置运行。

例如，下面的设置将强制 `Docker` 和 `Debugger for Chrome` 扩展远程运行，而不是它们默认的本地运行：

```json
"remote.extensionKind": {
    "msjsdiag.debugger-for-chrome": "workspace",
    "ms-azuretools.vscode-docker": "workspace"
}
```

值为 `"ui"` 而不是 `"workspace"` 将强制扩展在本地 UI/client 端运行。通常，这应该只用于测试，除非扩展文档中另有说明，因为**它会破坏扩展**。有关详细信息，请参阅关于 [支持远程开发](https://code.visualstudio.com/api/advanced-topics/remote-extensions) 的文章。

### 3. 转发一个端口 / 创建 SSH tunnel

有时在开发时，您可能需要访问远程机器上未公开的端口。有两种方法可以通过一个 [SSH tunnel](https://www.ssh.com/ssh/tunneling/example) 将所需的远程端口“转发”到本地计算机。

#### 3.1 临时转发一个端口

如果您想在会话期间**临时转发**一个新端口，当连接到活动 SSH 主机时请运行 `Remote-SSH: Forward Port from Active Host...` 命令。
![ssh](https://code.visualstudio.com/assets/docs/remote/ssh/forward-port-ssh.png)
输入端口号后，通知将告诉您应该使用哪个本地主机端口来访问远程端口。例如，如果您转发了一个监听端口 3000 的 HTTP 服务器，通知可能会告诉您它被映射到本地主机上的端口 4123。然后可以使用 [http://localhost:4123](http://localhost:4123/) 连接到这个远程 HTTP 服务器。

#### 3.2 总是转发一个端口

如果您有**总是希望转发**的端口，可以在上面的 [Remembering hosts](#14-%e8%ae%b0%e4%bd%8f%e4%bd%a0%e7%bb%8f%e5%b8%b8%e8%bf%9e%e6%8e%a5%e7%9a%84%e4%b8%bb%e6%9c%ba) 章节中创建的 SSH 配置文件中使用 `LocalForward` 指令。

例如，如果你想转发端口 `3000` 和 `27017`，你可以更新文件如下：

```txt
Host remote-linux-machine
    User myuser
    HostName remote-linux-machine.mydomain
    LocalForward 127.0.0.1:3000 127.0.0.1:3000
    LocalForward 127.0.0.1:27017 127.0.0.1:27017
```

### 4. 打开远程主机上的终端

从 VS Code 打开远程主机上的终端很简单。一旦连接上，在 VS Code 中打开的**任何终端窗口**(`Terminal > New Terminal`)都会自动运行在远程主机上，而不是本地。

您还可以使用来自这个终端窗口的 `code` 命令行来执行许多操作，例如打开远程主机上的新文件或文件夹。键入 `code --help` 查看命令行中可用的所有选项。
![ssh](https://code.visualstudio.com/assets/docs/remote/ssh/code-command-in-terminal.png)

### 5. 在 SSH 主机上调试

一旦连接到远程主机，就可以像在本地运行应用程序一样使用 VS Code 的调试器。例如，如果您在 `launch.json` 中选择了一个 launch 配置。然后启动调试(`F5`)，应用程序将在远程主机上启动并将调试器附加到它。

有关在 `.vscode/launch.json` 中配置 VS Code 调试特性的详细信息，请参阅 [调试](https://code.visualstudio.com/docs/editor/debugging) 文档。

### 6. SSH 主机特定的设置

当您连接到 SSH 主机时，VS Code 的本地用户设置也会被重用。虽然这可以保持用户体验的一致性，但是您可能希望在本地机器和每个主机之间更改这些设置。幸运的是，一旦连接到主机，还可以通过在命令面板(`F1`)上运行 `Preferences: Open Remote Settings` 命令或在 `settings editor` 中的 `Remote` 选项卡上进行选择来设置主机特定的设置。当您连接到主机时，这些设置将覆盖您现有的任何本地设置。
![ssh](https://code.visualstudio.com/assets/docs/remote/ssh/ssh-settings.png)

### 7. 使用本地工具工作

Remote - SSH 扩展不提供对同步源代码的直接支持，也不支持使用带有远程主机内容的本地工具。但是，有两种方法可以使用常见的工具来实现这一点，这些工具可以在大多数 Linux 主机上使用。具体地说,您可以：

- [使用 `SSHFS` 挂载远程文件系统。](https://code.visualstudio.com/docs/remote/troubleshooting#_using-sshfs-to-access-files-on-your-remote-host)
- [使用 `rsync` 将文件从远程主机同步到本地计算机或将文件从本地计算机同步到远程主机。](https://code.visualstudio.com/docs/remote/troubleshooting#_using-rsync-to-maintain-a-local-copy-of-your-source-code)

`SSHFS` 是最方便的选项，不需要任何文件同步。然而，性能将大大低于通过 VS Code 工作，所以**它最好用于单个文件编辑和上传/下载内容**。如果需要使用一次性批量读写多个文件的应用程序(如一个本地源代码控制工具)，`rsync` 是更好的选择。

### 8. 已知的限制

#### 8.1 Remote - SSH 限制

- 强烈建议使用基于密钥的身份验证。不保存为其他身份验证方法输入的密码和其他令牌。
- 还不支持 Windows 和 macOS SSH 主机(server)。(支持 Windows 和 macOS clients。)
- 不支持 Alpine Linux 和不是基于 `glibc` 的 Linux SSH 主机。
- 较旧的(社区支持的) Linux 发行版需要变通方法来安装 [所需的先决条件](https://code.visualstudio.com/docs/remote/linux)。
- Windows 上不支持 `PuTTY`。
- 如果您使用 SSH 克隆一个 Git 存储库，并且您的 SSH 密钥具有通行码(passphrase)，那么 VS Code 的 `pull` 和 `sync` 特性在远程运行时可能会挂起。要么使用没有 passphrase 的 SSH 密钥，要么使用 HTTPS 克隆，要么从命令行运行 `git push` 来解决这个问题。
- 本地代理设置不会在远程主机上重用，这可能会阻止扩展工作，除非在远程主机上配置了适当的代理信息(例如全局 `HTTP_PROXY` 或 `HTTPS_PROXY` 环境变量，其中包含适当的代理信息)。
- 有关 SSH 的活动问题的列表，请参见 [这里](https://aka.ms/vscode-remote/ssh/issues)。

#### 8.2 Docker 扩展限制

默认情况下，Docker 扩展被配置为作为本地 `"UI"` 扩展运行。当您在容器中开发时，这使扩展能够与本地 Docker 安装一起工作。但是，您可能想要将该扩展与安装在远程主机上的 Docker 机器一起使用。幸运的是，您可以将 Docker 扩展配置为在主机上运行，方法是在 `settings.json` 中添加以下内容：

```json
"remote.extensionKind": {
    "ms-azuretools.vscode-docker": "workspace"
}
```

#### 8.3 扩展限制

许多扩展无需修改就可以在远程 SSH 主机上工作。然而，在某些情况下，某些特性可能需要更改。如果您遇到扩展问题，在报告该问题时，您可以向扩展作者提及 [常见问题和解决方案的摘要](https://code.visualstudio.com/docs/remote/troubleshooting#_extension-tips)。

此外，安装在 `ARMv7l` 设备上的一些扩展可能无法工作，因为扩展中的本机模块或运行时只支持 `x86_64`。在这些情况下，扩展需要选择通过编译/包含用于 `ARMv7l` 的二进制文件来支持这些平台。

### 9. 常见问题

#### 9.1 如何在 XXX 上设置 SSH client？

有关详细信息，请参阅 [安装一个受支持的 SSH client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client)。

#### 9.2 如何在 XXX 上设置 SSH server？

有关为主机设置一个 SSH server 的详细信息，请参阅 [安装一个受支持的 SSH server](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-server)。

#### 9.3 我可以使用其他/额外的身份验证机制(比如密码)登录 SSH 服务器吗？

是的，系统会自动提示您输入令牌或密码。

然而，由于 [vscode-remote-release#642](https://github.com/microsoft/vscode-remote-release/issues/642)，您最终需要输入两次密码。在 SSH 配置中启用 `ControlMaster` 可能会有所帮助，但是我们在 Windows SSH client 上看到了混合的结果。有关正确设置的信息，请参阅 [启用备用 SSH 身份验证方法](https://code.visualstudio.com/docs/remote/troubleshooting#_enabling-alternate-ssh-authentication-methods)。

#### 9.4 如何修复关于 "bad permissions" 的 SSH 错误？

有关解决这些类型错误的详细信息，请参阅 [修复 SSH 文件权限错误](https://code.visualstudio.com/docs/remote/troubleshooting#_fixing-ssh-file-permission-errors)。

#### 9.5 需要在远程 SSH 主机上安装哪些 Linux 包/库？

大多数 Linux 发行版都不需要额外的依赖安装步骤。对于 SSH, Linux主机需要安装 `Bash(/bin/bash)`、`tar` 和 `curl` 或 `wget`，这些实用程序可能在某些简化发行版中丢失。远程开发还需要 `kernel >= 3.10`、`glibc >= 2.17`、`libstdc++ >= 3.4.18`。目前只支持基于 `glibc` 的发行版，因此扩展不支持 [Alpine Linux](https://alpinelinux.org/)。

有关详细信息，请参阅 [Linux 先决条件](https://code.visualstudio.com/docs/remote/linux)。

#### 9.6 当 VS Code Server 运行在一个 远程机器 / VM 上时，它的连接性要求是什么？

VS Code Server 需要出站 HTTPS(端口443) 连接到：

- `update.code.visualstudio.com`
- `marketplace.visualstudio.com`
- `vscode.blob.core.windows.net`
- `*.vo.msecnd.net` (Azure CDN)
- `*.gallerycdn.vsassets.io` (Azure CDN)

Server 和 VS Code Client 之间的所有其他通信都是通过一个经过身份验证的安全 SSH tunnel 完成的。您可以在 [“网络连接”文章](https://code.visualstudio.com/docs/setup/network#_common-hostnames) 中找到 VS Code 本身需要访问的位置列表。

最后，一些扩展(如 C# )从 `download.microsoft.com` 或 `download.visualstudio.microsoft.com` 下载次要依赖项。其他的(比如 [Visual Studio Live Share](https://docs.microsoft.com/visualstudio/liveshare/reference/connectivity#requirements-for-connection-modes))可能有额外的连接性需求。如果遇到麻烦，请参阅扩展的文档了解详细信息。

#### 9.7 我可以在远程 SSH 主机上的源代码上使用本地工具吗？

是的。通常，这是通过使用 [SSHFS](https://code.visualstudio.com/docs/remote/troubleshooting#_using-sshfs-to-access-files-on-your-remote-host) 或使用 [rsync](https://code.visualstudio.com/docs/remote/troubleshooting#_using-rsync-to-maintain-a-local-copy-of-your-source-code) 在本地机器上获取文件的副本来完成的。`SSHFS` 挂载远程文件系统非常适合于需要编辑单个文件或浏览源树且不需要使用同步步骤的场景。但是，对于使用诸如批量管理文件的源代码控制工具之类的工具来说，这并不理想。在这种情况下，`rsync` 方法更好，因为您可以在本地机器上获得远程源代码的完整副本。有关详细信息，请参阅 [提示和技巧](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/tips_tricks.md)。

#### 9.8 当我只有 SFTP/FTP 文件系统访问我的远程主机(没有 shell 访问)时，我可以使用 VS Code 吗？

有些云平台只为开发人员提供远程文件系统访问，而不提供直接的 shell 访问。 VS Code 远程开发并没有考虑到这个用例，因为它否定了性能和用户体验的好处。

但是，通常可以通过将 SFTP 之类的扩展与用于 [Node.js](https://code.visualstudio.com/docs/nodejs/nodejs-debugging#_remote-debugging)、[Python](https://code.visualstudio.com/docs/python/debugging#_remote-debugging)、[C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) 或其他的远程调试特性相结合来处理这个用例。

#### 9.9 作为一个扩展作者，我需要做什么？

 VS Code 扩展 API 抽象了本地/远程细节，因此大多数扩展无需修改即可工作。然而，给定的扩展可以使用任何节点模块或运行时，在某些情况下可能需要进行调整。我们建议您测试您的扩展，以确保不需要更新。有关详细信息，请参见 [支持远程开发](https://code.visualstudio.com/api/advanced-topics/remote-extensions)。

#### 9.10 问题或反馈

- 参见 [提示和技巧](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/tips_tricks.md) 或 [FAQ](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/faq.md)。
- 在 [Stack Overflow](https://stackoverflow.com/questions/tagged/vscode-remote) 上搜索。
- 添加一个 [特性请求](https://aka.ms/vscode-remote/feature-requests) 或 [报告一个问题](https://aka.ms/vscode-remote/issues/new)。
- 对 [我们的文档](https://github.com/Microsoft/vscode-docs) 或 [VS Code](https://github.com/Microsoft/vscode) 本身做出贡献。
- 详情请参阅我们的 [CONTRIBUTING](https://aka.ms/vscode-remote/contributing) 指南。
