<!--
 * @Author: haoluo
 * @Date: 2019-07-24 09:38:48
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-24 11:32:32
 * @Description: file content
 -->

- [远程开发提示和技巧](#%e8%bf%9c%e7%a8%8b%e5%bc%80%e5%8f%91%e6%8f%90%e7%a4%ba%e5%92%8c%e6%8a%80%e5%b7%a7)
  - [1. SSH 提示](#1-ssh-%e6%8f%90%e7%a4%ba)
    - [1.1 配置基于密钥的身份验证](#11-%e9%85%8d%e7%bd%ae%e5%9f%ba%e4%ba%8e%e5%af%86%e9%92%a5%e7%9a%84%e8%ba%ab%e4%bb%bd%e9%aa%8c%e8%af%81)
    - [1.2 快速开始：SSH 密钥](#12-%e5%bf%ab%e9%80%9f%e5%bc%80%e5%a7%8bssh-%e5%af%86%e9%92%a5)
    - [1.3 使用专用密钥(dedicated key)提高安全性](#13-%e4%bd%bf%e7%94%a8%e4%b8%93%e7%94%a8%e5%af%86%e9%92%a5dedicated-key%e6%8f%90%e9%ab%98%e5%ae%89%e5%85%a8%e6%80%a7)
    - [1.4 重用在 PuTTYGen 中生成的密钥](#14-%e9%87%8d%e7%94%a8%e5%9c%a8-puttygen-%e4%b8%ad%e7%94%9f%e6%88%90%e7%9a%84%e5%af%86%e9%92%a5)
    - [1.5 对挂起或失败的连接进行故障排除](#15-%e5%af%b9%e6%8c%82%e8%b5%b7%e6%88%96%e5%a4%b1%e8%b4%a5%e7%9a%84%e8%bf%9e%e6%8e%a5%e8%bf%9b%e8%a1%8c%e6%95%85%e9%9a%9c%e6%8e%92%e9%99%a4)
      - [1.5.1 查看 Vs Code 是否正在一个提示符(prompt)上等待](#151-%e6%9f%a5%e7%9c%8b-vs-code-%e6%98%af%e5%90%a6%e6%ad%a3%e5%9c%a8%e4%b8%80%e4%b8%aa%e6%8f%90%e7%a4%ba%e7%ac%a6prompt%e4%b8%8a%e7%ad%89%e5%be%85)
      - [1.5.2 在远程主机上启用 TCP 转发](#152-%e5%9c%a8%e8%bf%9c%e7%a8%8b%e4%b8%bb%e6%9c%ba%e4%b8%8a%e5%90%af%e7%94%a8-tcp-%e8%bd%ac%e5%8f%91)
      - [1.5.3 在您的 SSH 配置文件中设置 ProxyCommand 参数](#153-%e5%9c%a8%e6%82%a8%e7%9a%84-ssh-%e9%85%8d%e7%bd%ae%e6%96%87%e4%bb%b6%e4%b8%ad%e8%ae%be%e7%bd%ae-proxycommand-%e5%8f%82%e6%95%b0)
      - [1.5.4 确保远程机器能够访问 internet](#154-%e7%a1%ae%e4%bf%9d%e8%bf%9c%e7%a8%8b%e6%9c%ba%e5%99%a8%e8%83%bd%e5%a4%9f%e8%ae%bf%e9%97%ae-internet)
      - [1.5.5 在远程主机上设置 HTTP_PROXY / HTTPS_PROXY](#155-%e5%9c%a8%e8%bf%9c%e7%a8%8b%e4%b8%bb%e6%9c%ba%e4%b8%8a%e8%ae%be%e7%bd%ae-httpproxy--httpsproxy)
      - [1.5.6 使用 noexec 解决 /tmp 挂载](#156-%e4%bd%bf%e7%94%a8-noexec-%e8%a7%a3%e5%86%b3-tmp-%e6%8c%82%e8%bd%bd)
      - [1.5.7 检查安装期间是否启动了一个不同的 shell](#157-%e6%a3%80%e6%9f%a5%e5%ae%89%e8%a3%85%e6%9c%9f%e9%97%b4%e6%98%af%e5%90%a6%e5%90%af%e5%8a%a8%e4%ba%86%e4%b8%80%e4%b8%aa%e4%b8%8d%e5%90%8c%e7%9a%84-shell)
      - [1.5.8 连接到为每个连接动态分配机器的系统](#158-%e8%bf%9e%e6%8e%a5%e5%88%b0%e4%b8%ba%e6%af%8f%e4%b8%aa%e8%bf%9e%e6%8e%a5%e5%8a%a8%e6%80%81%e5%88%86%e9%85%8d%e6%9c%ba%e5%99%a8%e7%9a%84%e7%b3%bb%e7%bb%9f)
      - [1.5.9 请与系统管理员联系以获得配置帮助](#159-%e8%af%b7%e4%b8%8e%e7%b3%bb%e7%bb%9f%e7%ae%a1%e7%90%86%e5%91%98%e8%81%94%e7%b3%bb%e4%bb%a5%e8%8e%b7%e5%be%97%e9%85%8d%e7%bd%ae%e5%b8%ae%e5%8a%a9)
    - [1.6启用备用 SSH 身份验证方法](#16%e5%90%af%e7%94%a8%e5%a4%87%e7%94%a8-ssh-%e8%ba%ab%e4%bb%bd%e9%aa%8c%e8%af%81%e6%96%b9%e6%b3%95)
    - [1.7 设置 SSH 代理](#17-%e8%ae%be%e7%bd%ae-ssh-%e4%bb%a3%e7%90%86)
      - [1.7.1 Windows:](#171-windows)
      - [1.7.2 Linux:](#172-linux)
      - [1.7.3 macOS:](#173-macos)
    - [1.8 修复 SSH 文件权限错误](#18-%e4%bf%ae%e5%a4%8d-ssh-%e6%96%87%e4%bb%b6%e6%9d%83%e9%99%90%e9%94%99%e8%af%af)
    - [1.9 本地 SSH 文件和文件夹权限](#19-%e6%9c%ac%e5%9c%b0-ssh-%e6%96%87%e4%bb%b6%e5%92%8c%e6%96%87%e4%bb%b6%e5%a4%b9%e6%9d%83%e9%99%90)
      - [1.9.1 macOS / Linux：](#191-macos--linux)
      - [1.9.2 Windows：](#192-windows)
    - [1.10 Server SSH 文件和文件夹权限](#110-server-ssh-%e6%96%87%e4%bb%b6%e5%92%8c%e6%96%87%e4%bb%b6%e5%a4%b9%e6%9d%83%e9%99%90)
    - [1.11 安装一个受支持的 SSH Client](#111-%e5%ae%89%e8%a3%85%e4%b8%80%e4%b8%aa%e5%8f%97%e6%94%af%e6%8c%81%e7%9a%84-ssh-client)
    - [1.12 安装一个受支持的 SSH Server](#112-%e5%ae%89%e8%a3%85%e4%b8%80%e4%b8%aa%e5%8f%97%e6%94%af%e6%8c%81%e7%9a%84-ssh-server)
    - [1.13 解决在 SSH 主机上执行 Git push 或 sync 时挂起的问题](#113-%e8%a7%a3%e5%86%b3%e5%9c%a8-ssh-%e4%b8%bb%e6%9c%ba%e4%b8%8a%e6%89%a7%e8%a1%8c-git-push-%e6%88%96-sync-%e6%97%b6%e6%8c%82%e8%b5%b7%e7%9a%84%e9%97%ae%e9%a2%98)
    - [1.14 使用 SSHFS 访问远程主机上的文件](#114-%e4%bd%bf%e7%94%a8-sshfs-%e8%ae%bf%e9%97%ae%e8%bf%9c%e7%a8%8b%e4%b8%bb%e6%9c%ba%e4%b8%8a%e7%9a%84%e6%96%87%e4%bb%b6)
      - [1.14.1 macOS / Linux：](#1141-macos--linux)
      - [1.14.2 Windows：](#1142-windows)
    - [1.15 使用 rsync 维护源代码的本地副本](#115-%e4%bd%bf%e7%94%a8-rsync-%e7%bb%b4%e6%8a%a4%e6%ba%90%e4%bb%a3%e7%a0%81%e7%9a%84%e6%9c%ac%e5%9c%b0%e5%89%af%e6%9c%ac)
    - [1.16 清理远程上的 Vs Code 服务器](#116-%e6%b8%85%e7%90%86%e8%bf%9c%e7%a8%8b%e4%b8%8a%e7%9a%84-vs-code-%e6%9c%8d%e5%8a%a1%e5%99%a8)
  - [2. 容器技巧](#2-%e5%ae%b9%e5%99%a8%e6%8a%80%e5%b7%a7)
    - [2.1 Docker桌面的Windows提示](#21-docker%e6%a1%8c%e9%9d%a2%e7%9a%84windows%e6%8f%90%e7%a4%ba)
    - [2.2 在Docker桌面中启用文件共享](#22-%e5%9c%a8docker%e6%a1%8c%e9%9d%a2%e4%b8%ad%e5%90%af%e7%94%a8%e6%96%87%e4%bb%b6%e5%85%b1%e4%ba%ab)
      - [2.2.1 窗口:](#221-%e7%aa%97%e5%8f%a3)
      - [2.2.2 macOS:](#222-macos)
    - [2.3解决容器中的Git行结束问题(导致许多修改文件)](#23%e8%a7%a3%e5%86%b3%e5%ae%b9%e5%99%a8%e4%b8%ad%e7%9a%84git%e8%a1%8c%e7%bb%93%e6%9d%9f%e9%97%ae%e9%a2%98%e5%af%bc%e8%87%b4%e8%ae%b8%e5%a4%9a%e4%bf%ae%e6%94%b9%e6%96%87%e4%bb%b6)
    - [2.4 使用Docker组合时，避免在容器中设置Git](#24-%e4%bd%bf%e7%94%a8docker%e7%bb%84%e5%90%88%e6%97%b6%e9%81%bf%e5%85%8d%e5%9c%a8%e5%ae%b9%e5%99%a8%e4%b8%ad%e8%ae%be%e7%bd%aegit)
    - [2.5 在从容器执行Git推送或同步时解决挂起问题](#25-%e5%9c%a8%e4%bb%8e%e5%ae%b9%e5%99%a8%e6%89%a7%e8%a1%8cgit%e6%8e%a8%e9%80%81%e6%88%96%e5%90%8c%e6%ad%a5%e6%97%b6%e8%a7%a3%e5%86%b3%e6%8c%82%e8%b5%b7%e9%97%ae%e9%a2%98)
    - [2.6 解决关于缺少Linux依赖项的错误](#26-%e8%a7%a3%e5%86%b3%e5%85%b3%e4%ba%8e%e7%bc%ba%e5%b0%91linux%e4%be%9d%e8%b5%96%e9%a1%b9%e7%9a%84%e9%94%99%e8%af%af)
    - [2.7 加速Docker桌面中的容器](#27-%e5%8a%a0%e9%80%9fdocker%e6%a1%8c%e9%9d%a2%e4%b8%ad%e7%9a%84%e5%ae%b9%e5%99%a8)
    - [2.8 清理未使用的容器和图像](#28-%e6%b8%85%e7%90%86%e6%9c%aa%e4%bd%bf%e7%94%a8%e7%9a%84%e5%ae%b9%e5%99%a8%e5%92%8c%e5%9b%be%e5%83%8f)
    - [2.9 解决Dockerfile构建失败的图像使用Debian 8](#29-%e8%a7%a3%e5%86%b3dockerfile%e6%9e%84%e5%bb%ba%e5%a4%b1%e8%b4%a5%e7%9a%84%e5%9b%be%e5%83%8f%e4%bd%bf%e7%94%a8debian-8)
    - [2.10 在使用电子邮件时解决Docker集线器符号错误](#210-%e5%9c%a8%e4%bd%bf%e7%94%a8%e7%94%b5%e5%ad%90%e9%82%ae%e4%bb%b6%e6%97%b6%e8%a7%a3%e5%86%b3docker%e9%9b%86%e7%ba%bf%e5%99%a8%e7%ac%a6%e5%8f%b7%e9%94%99%e8%af%af)
    - [2.11 Hyperkit在macOS上的高CPU利用率](#211-hyperkit%e5%9c%a8macos%e4%b8%8a%e7%9a%84%e9%ab%98cpu%e5%88%a9%e7%94%a8%e7%8e%87)
    - [2.12 高级容器配置技巧](#212-%e9%ab%98%e7%ba%a7%e5%ae%b9%e5%99%a8%e9%85%8d%e7%bd%ae%e6%8a%80%e5%b7%a7)
  - [3. WSL的技巧](#3-wsl%e7%9a%84%e6%8a%80%e5%b7%a7)
    - [3.1 选择远程WSL使用的默认分布](#31-%e9%80%89%e6%8b%a9%e8%bf%9c%e7%a8%8bwsl%e4%bd%bf%e7%94%a8%e7%9a%84%e9%bb%98%e8%ae%a4%e5%88%86%e5%b8%83)
    - [3.2 Vs Code 服务器启动时挂起](#32-vs-code-%e6%9c%8d%e5%8a%a1%e5%99%a8%e5%90%af%e5%8a%a8%e6%97%b6%e6%8c%82%e8%b5%b7)
    - [3.3 修复代码命令无法工作的问题](#33-%e4%bf%ae%e5%a4%8d%e4%bb%a3%e7%a0%81%e5%91%bd%e4%bb%a4%e6%97%a0%e6%b3%95%e5%b7%a5%e4%bd%9c%e7%9a%84%e9%97%ae%e9%a2%98)
    - [3.4 解决关于丢失依赖项的错误](#34-%e8%a7%a3%e5%86%b3%e5%85%b3%e4%ba%8e%e4%b8%a2%e5%a4%b1%e4%be%9d%e8%b5%96%e9%a1%b9%e7%9a%84%e9%94%99%e8%af%af)
    - [3.5 解决WSL中的Git行结束问题(导致许多修改文件)](#35-%e8%a7%a3%e5%86%b3wsl%e4%b8%ad%e7%9a%84git%e8%a1%8c%e7%bb%93%e6%9d%9f%e9%97%ae%e9%a2%98%e5%af%bc%e8%87%b4%e8%ae%b8%e5%a4%9a%e4%bf%ae%e6%94%b9%e6%96%87%e4%bb%b6)
    - [3.6 在从WSL执行Git推送或同步时解决挂起问题](#36-%e5%9c%a8%e4%bb%8ewsl%e6%89%a7%e8%a1%8cgit%e6%8e%a8%e9%80%81%e6%88%96%e5%90%8c%e6%ad%a5%e6%97%b6%e8%a7%a3%e5%86%b3%e6%8c%82%e8%b5%b7%e9%97%ae%e9%a2%98)
  - [4. 扩展提示](#4-%e6%89%a9%e5%b1%95%e6%8f%90%e7%a4%ba)
    - [4.1 远程应用时，本地绝对路径设置失败](#41-%e8%bf%9c%e7%a8%8b%e5%ba%94%e7%94%a8%e6%97%b6%e6%9c%ac%e5%9c%b0%e7%bb%9d%e5%af%b9%e8%b7%af%e5%be%84%e8%ae%be%e7%bd%ae%e5%a4%b1%e8%b4%a5)
    - [4.2 需要在远程端点上安装本地VSIX](#42-%e9%9c%80%e8%a6%81%e5%9c%a8%e8%bf%9c%e7%a8%8b%e7%ab%af%e7%82%b9%e4%b8%8a%e5%ae%89%e8%a3%85%e6%9c%ac%e5%9c%b0vsix)
    - [4.3 浏览器不能在本地打开](#43-%e6%b5%8f%e8%a7%88%e5%99%a8%e4%b8%8d%e8%83%bd%e5%9c%a8%e6%9c%ac%e5%9c%b0%e6%89%93%e5%bc%80)
    - [4.4 剪贴板无法工作](#44-%e5%89%aa%e8%b4%b4%e6%9d%bf%e6%97%a0%e6%b3%95%e5%b7%a5%e4%bd%9c)
    - [4.5 无法从浏览器或应用程序访问本地web服务器](#45-%e6%97%a0%e6%b3%95%e4%bb%8e%e6%b5%8f%e8%a7%88%e5%99%a8%e6%88%96%e5%ba%94%e7%94%a8%e7%a8%8b%e5%ba%8f%e8%ae%bf%e9%97%ae%e6%9c%ac%e5%9c%b0web%e6%9c%8d%e5%8a%a1%e5%99%a8)
    - [4.6 不显示WebView内容](#46-%e4%b8%8d%e6%98%be%e7%a4%bawebview%e5%86%85%e5%ae%b9)
    - [4.7 阻塞本地主机端口](#47-%e9%98%bb%e5%a1%9e%e6%9c%ac%e5%9c%b0%e4%b8%bb%e6%9c%ba%e7%ab%af%e5%8f%a3)
    - [4.8 存储扩展数据的错误](#48-%e5%ad%98%e5%82%a8%e6%89%a9%e5%b1%95%e6%95%b0%e6%8d%ae%e7%9a%84%e9%94%99%e8%af%af)
    - [4.9 每次连接到新端点时都不能登录/必须登录](#49-%e6%af%8f%e6%ac%a1%e8%bf%9e%e6%8e%a5%e5%88%b0%e6%96%b0%e7%ab%af%e7%82%b9%e6%97%b6%e9%83%bd%e4%b8%8d%e8%83%bd%e7%99%bb%e5%bd%95%e5%bf%85%e9%a1%bb%e7%99%bb%e5%bd%95)
    - [4.10 不兼容的扩展阻止 Vs Code 连接](#410-%e4%b8%8d%e5%85%bc%e5%ae%b9%e7%9a%84%e6%89%a9%e5%b1%95%e9%98%bb%e6%ad%a2-vs-code-%e8%bf%9e%e6%8e%a5)
    - [4.11 交付或获取预先构建的本机模块的扩展会失败](#411-%e4%ba%a4%e4%bb%98%e6%88%96%e8%8e%b7%e5%8f%96%e9%a2%84%e5%85%88%e6%9e%84%e5%bb%ba%e7%9a%84%e6%9c%ac%e6%9c%ba%e6%a8%a1%e5%9d%97%e7%9a%84%e6%89%a9%e5%b1%95%e4%bc%9a%e5%a4%b1%e8%b4%a5)
    - [4.12 扩展只在非x86_64主机或Alpine Linux上失败](#412-%e6%89%a9%e5%b1%95%e5%8f%aa%e5%9c%a8%e9%9d%9ex8664%e4%b8%bb%e6%9c%ba%e6%88%96alpine-linux%e4%b8%8a%e5%a4%b1%e8%b4%a5)
    - [4.13 扩展由于缺少模块而失败](#413-%e6%89%a9%e5%b1%95%e7%94%b1%e4%ba%8e%e7%bc%ba%e5%b0%91%e6%a8%a1%e5%9d%97%e8%80%8c%e5%a4%b1%e8%b4%a5)
    - [4.14 无法访问/传输远程工作区文件到本地计算机](#414-%e6%97%a0%e6%b3%95%e8%ae%bf%e9%97%ae%e4%bc%a0%e8%be%93%e8%bf%9c%e7%a8%8b%e5%b7%a5%e4%bd%9c%e5%8c%ba%e6%96%87%e4%bb%b6%e5%88%b0%e6%9c%ac%e5%9c%b0%e8%ae%a1%e7%ae%97%e6%9c%ba)
    - [4.15 无法从扩展访问附加设备](#415-%e6%97%a0%e6%b3%95%e4%bb%8e%e6%89%a9%e5%b1%95%e8%ae%bf%e9%97%ae%e9%99%84%e5%8a%a0%e8%ae%be%e5%a4%87)
  - [5. 问题和反馈](#5-%e9%97%ae%e9%a2%98%e5%92%8c%e5%8f%8d%e9%a6%88)

## 远程开发提示和技巧

本文介绍了针对每个 Visual Studio Code [远程开发](https://aka.ms/vscode-remote/download/extension) 扩展的故障排除提示和技巧。有关设置和使用每个特定扩展的详细信息，请参阅 [SSH](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/ssh.md)、[Containers](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/containers.md) 和 [WSL](https://love2.io/@lh786020019/doc/VS-Code-docs/remote/wsl.md) 文章。

### 1. SSH 提示

#### 1.1 配置基于密钥的身份验证

[SSH 公钥身份验证](https://www.ssh.com/ssh/public-key-authentication) 是一种方便、高安全性的身份验证方法，它结合了**本地“私有”密钥**和与在 SSH 主机上的您的用户帐户关联的**“公共”密钥**。本节将介绍如何生成这些密钥并将它们添加到主机。

提示：PuTTY for Windows 不是一个受支持的 client，但是您可以[转换您的 PuTTYGen 密钥](https://code.visualstudio.com/docs/remote/troubleshooting#_reusing-a-key-generated-in-puttygen)。

#### 1.2 快速开始：SSH 密钥

要为远程主机设置基于 SSH 密钥的身份验证:

1. 检查**本地**计算机上是否已经有 SSH 密钥。公钥在 macOS / Linux 上通常位于 `~/.ssh/id_rsa.pub`，在 Windows 上通常位于  `%USERPROFILE%\.ssh\id_rsa.pub`。

    如果没有密钥，在**本地**终端/命令提示符中运行以下命令，生成一个 SSH 密钥对：

    ```shell
    ssh-keygen -t rsa -b 4096
    ```

    > 提示：没有 `ssh-keygen`？安装 [一个受支持的 SSH client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client)。

2. 添加您本地公钥（ `id_rsa.pub` 文件）的内容到 SSH 主机上适当的 `authorized_keys` 文件。

    在 **macOS/Linux** 上，在**本地终端**中运行以下命令，根据需要替换 `user name` 和 `host name`。

    ```shell
    ssh-copy-id your-user-name-on-host@host-fqdn-or-ip-goes-here
    ```

    在 **Windows** 上，在一个**本地命令提示符**中运行以下命令，根据需要替换 `REMOTEHOST` 的值。

    ```shell
    SET REMOTEHOST=your-user-name-on-host@host-fqdn-or-ip-goes-here

    scp %USERPROFILE%\.ssh\id_rsa.pub %REMOTEHOST%:~/tmp.pub
    ssh %REMOTEHOST% "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat ~/tmp.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f ~/tmp.pub"
    ```

#### 1.3 使用专用密钥(dedicated key)提高安全性

虽然在所有 SSH 主机之间使用一个 SSH 密钥很方便，但是如果任何人获得了对您的私钥的访问权，那么他们也可以访问您的所有主机。可以通过为您的开发主机创建特定的 SSH 密钥来防止这种情况。只需遵循以下步骤：

1. 在一个不同的文件中生成一个特定的 SSH 密钥。

    在 **macOS / Linux** 上，在**本地终端**运行以下命令：

    ```shell
    ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa-remote-ssh
    ```

    在 **Windows** 上，在**本地命令提示符**中运行以下命令：

    ```shell
    ssh-keygen -t rsa -b 4096 -f %USERPROFILE%\.ssh\id_rsa-remote-ssh
    ```

2. 在 Vs Code 中，在命令面板(`F1`)中运行 `Remote-SSH: Open Configuration File...`，选择一个 SSH 配置文件，并按如下方式添加(或修改)一个主机条目：

    ```txt
    Host name-of-ssh-host-here
        User your-user-name-on-host
        HostName host-fqdn-or-ip-goes-here
        IdentityFile ~/.ssh/id_rsa-remote-ssh
    ```

3. 将步骤 1 中生成的本地 `id_rsa-remote-ssh.pub` 文件的内容添加到 **SSH 主机**上适当的 `authorized_keys` 文件。

    在 **macOS / Linux** 上，在**本地终端**上运行以下命令，将 `name-of-ssh-host-here` 替换为步骤 2 设置的 SSH 配置文件中的 `host name`：

    ```shell
    ssh-copy-id -i ~/.ssh/id_rsa-remote-ssh.pub name-of-ssh-host-here
    ```

    在 **Windows** 上，在**本地命令提示符**中运行以下命令，将 `name-of-ssh-host-here` 替换为步骤 2 设置的 SSH 配置文件中的 `host name`：

    ```shell
    SET REMOTEHOST=name-of-ssh-host-here
    SET PATHOFIDENTITYFILE=%USERPROFILE%\.ssh\id_rsa-remote-ssh.pub

    scp %PATHOFIDENTITYFILE% %REMOTEHOST%:~/tmp.pub
    ssh %REMOTEHOST% "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat ~/tmp.pub >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys && rm -f ~/tmp.pub"
    ```

#### 1.4 重用在 PuTTYGen 中生成的密钥

如果您使用 `PuTTYGen` 为要连接的主机设置 SSH 公钥身份验证，则您需要转换您的私钥，以便其他 SSH client 可以使用它。要做到这一点：

1. 在**本地**打开 `PuTTYGen` 并加载要转换的私钥。
2. 从应用程序菜单中选择 `Conversions > Export OpenSSH key`，将转换后的密钥保存到**本地**位置，例如 `%USERPROFILE%\.ssh`。
3. 验证导出的密钥文件上的**本地**权限，只将 **完全控制(Full Control)** 授予您的用户、Administrators 和 SYSTEM。
4. 在 Vs Code 中，在命令面板(`F1`)中运行 `Remote-SSH: Open Configuration File...`，选择一个您想更改的 SSH 配置文件，并在配置文件中添加(或修改)一个主机条目，如下所示：

    ```txt
    Host name-of-ssh-host-here
        User your-user-name-on-host
        HostName host-fqdn-or-ip-goes-here
        IdentityFile C:\path\to\your\exported\private\keyfile
    ```

#### 1.5 对挂起或失败的连接进行故障排除

如果您在尝试连接时遇到 Vs Code 挂起(hanging)的问题(并且可能超时)，您可以做一些事情来尝试解决这个问题。

##### 1.5.1 查看 Vs Code 是否正在一个提示符(prompt)上等待

在 Vs Code 中启用 `remote.SSH.showLoginTerminal` [设置](https://love2.io/@lh786020019/doc/VS-Code-docs/get_started/settings.md) 并重试。如果提示您输入一个密码或令牌，请参阅 [启用备用 SSH 身份验证方法](https://code.visualstudio.com/docs/remote/troubleshooting#_enabling-alternate-ssh-authentication-methods) 以了解有关减少提示频率的详细信息。

##### 1.5.2 在远程主机上启用 TCP 转发

Remote - SSH 扩展使用 SSH tunnel 来促进与主机的通信。在某些情况下，这可能在 SSH server 上禁用。要查看是否存在此问题，请在输出窗口中打开 `Remote - SSH` 类别，并检查以下消息：

```txt
open failed: administratively prohibited: open failed
```

如果您确实看到该消息，请按照以下步骤更新您的 SSH server 的 [sshd 配置](https://www.ssh.com/ssh/sshd_config/):

1. 在 **SSH 主机**(不是本地的)上的一个编辑器(如 `vim`、`nano` 或 `pico`)中打开 `/etc/ssh/sshd_config` 文件。
2. 添加设置 `AllowTcpForwarding yes`。
3. 重启 SSH server（在 Ubuntu 上运行 `sudo systemctl restart sshd`）。
4. 重试。

##### 1.5.3 在您的 SSH 配置文件中设置 ProxyCommand 参数

如果您在代理的后面，并且无法连接到 SSH 主机，那么您可能需要在**本地** [SSH 配置文件](https://linux.die.net/man/5/ssh_config) 中为您的主机使用 `ProxyCommand` 参数。您可以阅读这篇 [SSH ProxyCommand 文章](https://www.cyberciti.biz/faq/linux-unix-ssh-proxycommand-passing-through-one-host-gateway-server/)，了解它的使用示例。

##### 1.5.4 确保远程机器能够访问 internet

远程机器必须能够访问 internet 才能从市场下载 Vs Code Server 和扩展。有关连接需求的详细信息，请参阅 [FAQ](https://code.visualstudio.com/docs/remote/faq#_what-are-the-connectivity-requirements-for-vs-code-server)。

##### 1.5.5 在远程主机上设置 HTTP_PROXY / HTTPS_PROXY

如果您的远程主机位于代理的后面，您可能需要在 SSH 主机上设置 `HTTP_PROXY` 或 `HTTPS_PROXY` 环境变量。打开你的 `~/.bashrc` 文件添加以下内容（替换 `proxy.fqdn.or.ip:3128` 为适当的 `hostname/IP` 和 `port`）：

```shell
export HTTP_PROXY=http://proxy.fqdn.or.ip:3128
export HTTPS_PROXY=$HTTP_PROXY

# Or if an authenticated proxy
export HTTP_PROXY=http://username:password@proxy.fqdn.or.ip:3128
export HTTPS_PROXY=$HTTP_PROXY
```

##### 1.5.6 使用 noexec 解决 /tmp 挂载

一些远程服务器被设置为不允许从 `/tmp` 执行脚本。VS Code 将其安装脚本写入系统临时目录，并尝试从那里执行它。您可以与系统管理员一起确定是否可以解决此问题。

##### 1.5.7 检查安装期间是否启动了一个不同的 shell

有些用户在 **SSH 主机**上启动了一个与 `.bash_profile` 或其他启动脚本不同的 shell，因为他们希望使用与默认不同的shell。这可能会破坏 VS Code 的远程服务器安装脚本，不建议这样做。代替的是，使用 `chsh` 更改远程机器上的默认 shell。

##### 1.5.8 连接到为每个连接动态分配机器的系统

有些系统会在每次建立 SSH 连接时动态地将 SSH 连接从集群路由到一个节点。这是 Vs Code 的问题,因为它使两个连接打开一个远程窗口：第一个安装或启动 Vs Code 服务器(或找到一个已经运行的实例)和第二创建 SSH 端口隧道 Vs Code 使用与服务器。如果 Vs Code 在创建第二个连接时路由到另一台机器，那么它将无法与 Vs Code 服务器通信。

对此的一种解决方案是在 OpenSSH(仅 macOS/Linux client) 中使用 `ControlMaster` 选项，该选项在启用备用 SSH 身份验证方法中进行了描述，这样 Vs Code 的两个连接将通过同一个节点的单个 SSH 连接进行多路传输。

##### 1.5.9 请与系统管理员联系以获得配置帮助

SSH 是一种非常灵活的协议，支持多种配置。如果在登录终端或远程 ssh 输出窗口中看到其他错误，可能是由于缺少设置造成的。

有关 SSH 主机和客户机所需设置的信息，请与系统管理员联系。可以将连接到SSH主机的特定命令行参数添加到SSH配置文件中。

要访问配置文件，请在命令面板(F1)中运行 `Remote-SSH: Open Configuration file…`。然后，您可以与管理员一起添加必要的设置。

#### 1.6启用备用 SSH 身份验证方法

如果您正在连接到 SSH 远程主机，并且是:

- 与双因素身份验证连接，
- 使用密码身份验证,
- 当 SSH 代理不运行或无法访问时，使用带有密码的SSH密钥，

… Vs Code 应该自动提示您输入所需的信息。如果没有看到提示符，请在 Vs Code 设置中启用 `remote.SSH.showLoginTerminal`。当 Vs Code 运行 SSH 命令时，此设置将显示终端。然后，当终端出现时，您可以输入您的认证代码、密码或通行码。

但是，由于 [vscode-remote-release#642](https://github.com/microsoft/vscode-remote-release/issues/642)，可能会多次提示您输入此信息。在 macOS 和 Linux 上，可以通过在本地机器上启用 `ControlMaster` 特性来避免这个问题，这样 OpenSSH 就可以在一个连接上运行多个 SSH 会话。启用 `ControlMaster`:

1. 在 SSH 配置文件中添加这样一个条目：

    ```txt
    Host *
        ControlMaster auto
        ControlPath  ~/.ssh/sockets/%r@%h-%p
        ControlPersist  600
    ```

2. 然后运行 `mkdir -p ~/.ssh/sockets` 创建套接字文件夹。

启用 `ControlMaster` 后，您只需输入一次认证代码/密码/通行码。

#### 1.7 设置 SSH 代理

如果使用带密码的密钥连接到 SSH 主机，应该确保 SSH 代理在本地运行。Vs Code 将自动将您的密钥添加到代理，这样您就不必每次打开远程 Vs Code 窗口时都输入密码。

要验证代理正在运行并且可以从 Vs Code 的环境中访问，可以在本地 Vs Code 窗口的终端中运行 `ssh-add -l`。您应该看到代理中键的列表(或者没有键的消息)。如果代理没有运行，请按照以下指示启动它。启动代理之后，请确保重新启动 Vs Code 。

##### 1.7.1 Windows:

要在 Windows 上自动启用 SSH 代理，请以**管理员身份**启动 PowerShell 并运行以下命令：

```shell
# Make sure you're running as an Administrator
Set-Service ssh-agent -StartupType Automatic
Start-Service ssh-agent
Get-Service ssh-agent
```

现在代理将在登录时自动启动。

##### 1.7.2 Linux:

要在后台启动 SSH 代理，运行：

```shell
eval "$(ssh-agent -s)"
```

要在登录时自动启动 SSH 代理，请将以下行添加到 `~/.bash_profile`：

```bash
if [ -z "$SSH_AUTH_SOCK" ]
then
   # Check for a currently running instance of the agent
   RUNNING_AGENT="`ps -ax | grep 'ssh-agent -s' | grep -v grep | wc -l | tr -d '[:space:]'`"
   if [ "$RUNNING_AGENT" = "0" ]
   then
        # Launch a new instance of the agent
        ssh-agent -s &> .ssh/ssh-agent
   fi
   eval `cat .ssh/ssh-agent`
fi
```

##### 1.7.3 macOS:

默认情况下，代理应该在 macOS 上运行。

#### 1.8 修复 SSH 文件权限错误

SSH 可以严格控制文件权限，如果设置不正确，您可能会看到诸如 `"WARNING: UNPROTECTED PRIVATE KEY FILE!"` 的错误，有几种方法可以更新文件权限来解决这个问题，下面的小节将对此进行描述。

#### 1.9 本地 SSH 文件和文件夹权限

##### 1.9.1 macOS / Linux：

在本地计算机上，请确保设置了以下权限：

|Folder / File | Permissions |
|--|--|
|`.ssh` in your user folder|`chmod 700 ~/.ssh`|
|`.ssh/config` in your user folder|`chmod 600 ~/.ssh/config`|
|`.ssh/id_rsa.pub` in your user folder|`chmod 600 ~/.ssh/id_rsa.pub`|
|Any other key file|`chmod 600 /path/to/key/file`|

##### 1.9.2 Windows：

特定的预期权限可以根据您使用的 SSH 实现的具体情况而变化。我们强烈建议使用开箱即用的 [Windows 10 OpenSSH Client](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview)。如果您正在使用这个官方客户端，请在 **administrator PowerShell 窗口**中剪切并粘贴以下内容，以尝试修复您的权限：

```shell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process

Install-Module -Force OpenSSHUtils -Scope AllUsers

Repair-UserSshConfigPermission ~/.ssh/config
Get-ChildItem ~\.ssh\* -Include "id_rsa","id_dsa" -ErrorAction SilentlyContinue | % {
    Repair-UserKeyPermission -FilePath $_.FullName @psBoundParameters
}
```

对于所有其他 Client，请参考您的 Client 文档了解要实现的期望。但是，请注意，并非所有 SSH Client 都可以工作。

#### 1.10 Server SSH 文件和文件夹权限

在要连接的远程计算机上，请确保设置了以下权限：

|Folder / File|Linux / macOS Permissions|
|--|--|
|`.ssh` in your user folder on the server|`chmod 700 ~/.ssh`|
|`.ssh/authorized_keys` in your user folder on the server|`chmod 600 ~/.ssh/authorized_keys`|

注意，目前只支持 Linux 主机，这就是为什么省略了 macOS 和 Windows 10 的权限。

#### 1.11 安装一个受支持的 SSH Client

|OS|Instructions|
|--|--|
|Windows 10 / Server 2016|Install the [Windows OpenSSH Client](https://docs.microsoft.com/windows-server/administration/openssh/openssh_install_firstuse).|
|Earlier Windows|Install [Git for Windows](https://git-scm.com/download/win).|
|macOS|Comes pre-installed.|
|Debian/Ubuntu|Run `sudo apt-get install openssh-client`|
|RHEL / Fedora / CentOS|Run `sudo yum install openssh-clients`|

 Vs Code 将在路径中寻找 `ssh` 命令。如果没有找到，在 Windows 上它将尝试从 Windows 安装路径的默认 Git 中选择 `ssh.exe`。您还可以通过添加 `remote.SSH.path` 属性设置到 `settings.json` 来明确告诉 Vs Code 在哪里可以找到 SSH Client。

#### 1.12 安装一个受支持的 SSH Server

|OS|Instructions|Details|
|--|--|--|
|Debian 8+ / Ubuntu 16.04+|Run `sudo apt-get install openssh-server`|See the [Ubuntu SSH](https://help.ubuntu.com/community/SSH?action=show) documentation for details.|
|RHEL / CentOS 7+|Run `sudo yum install openssh-server && sudo systemctl start sshd.service && sudo systemctl enable sshd.service`|See the [RedHat SSH](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/ch-openssh) documentation for details.|
|SuSE 12+ / openSUSE 42.3+|In Yast, go to Services Manager, select "sshd" in the list, and click **Enable**. Next go to Firewall, select the **Permanent** configuration, and under services check **sshd**.|See the [SuSE SSH](https://en.opensuse.org/OpenSSH) documentation for details.|
|Windows|Not supported yet.|
|macOS|Not supported yet.|

#### 1.13 解决在 SSH 主机上执行 Git push 或 sync 时挂起的问题

如果您使用 SSH 克隆 Git 存储库，并且您的 SSH 密钥具有通行码，那么 Vs Code 的 pull 和 sync 特性在远程运行时可能会挂起。

要么使用没有通行码的 SSH 密钥，要么使用 HTTPS 克隆，要么从命令行运行 `git push` 来解决这个问题。

#### 1.14 使用 SSHFS 访问远程主机上的文件

[SSHFS](https://en.wikipedia.org/wiki/SSHFS) 是一种基于 `SFTP` 构建的安全远程文件系统访问协议。与 `CIFS/Samba` 共享相比，它提供了一些优势，因为所需要的只是对机器的 SSH 访问。

> 注意：出于性能原因，`SSHFS` 最适合用于单个文件编辑和上载/下载内容。如果需要使用一次性批量读写多个文件的应用程序(如本地源代码控制工具)，[rsync](https://code.visualstudio.com/docs/remote/troubleshooting#_using-rsync-to-maintain-a-local-copy-of-your-source-code) 是更好的选择。

##### 1.14.1 macOS / Linux：

在 Linux 上，可以使用发行版的包管理器安装 `SSHFS`。对于 `Debian/Ubuntu`：`sudo apt-get install sshfs`

> 注意：**WSL 1** 不支持 `FUSE` 或 `SSHFS`，因此目前针对 Windows 的指令有所不同。**WSL2** 确实包括 `FUSE` 和 `SSHFS` 支持，所以很快就会改变。

在 macOS 上，您可以使用 [Homebrew](https://brew.sh/) 安装 `SSHFS`：`brew install sshfs`。另外，如果您不希望使用命令行来安装远程文件系统，您还可以安装 [SSHFS GUI](https://github.com/dstuecken/sshfs-gui)。

要使用命令行，从本地终端运行以下命令(用远程用户和 hostname/IP 替换 `user@hostname`)：

```shell
export USER_AT_HOST=user@hostname
# Make the directory where the remote filesystem will be mounted
mkdir -p "$HOME/sshfs/$USER_AT_HOST"
# Mount the remote filesystem
sshfs "$USER_AT_HOST:" "$HOME/sshfs/$USER_AT_HOST" -ovolname="$USER_AT_HOST" -p 22  \
    -o workaround=nonodelay -o transform_symlinks -o idmap=user  -C
```

这将使远程机器上的主文件夹在 `~/sshfs` 下可用。完成后，您可以使用 OS 的 Finder / file explorer 或使用命令行卸载它：

```shell
umount "$HOME/sshfs/$USER_AT_HOST"
```

##### 1.14.2 Windows：

遵循以下步骤：

1. 在 Linux 上，将 `.gitattributes` 文件添加到您的项目中，以强制 Linux 和 Windows 之间**保持一致的行尾**，以避免由于两个操作系统之间的 `CRLF/LF` 差异而导致的意外问题。有关详细信息，请参见 [解决 Git 行结束问题](https://code.visualstudio.com/docs/remote/troubleshooting#_resolving-git-line-ending-issues-in-wsl-resulting-in-many-modified-files)。
2. 接下来，使用 [Chocolatey](https://chocolatey.org/) 安装 [SSHFS-Win](https://github.com/billziss-gh/sshfs-win)：`choco install sshfs`
3. 一旦为 Windows 安装了 `SSHFS`，就可以使用文件资源管理器的 `Map Network Drive...` 选项，路径 `\\sshfs\user@hostname`，其中 `user@hostname` 是您的远程用户和 hostname/IP。您可以使用如下命令提示符编写脚本：`net use /PERSISTENT:NO X: \\sshfs\user@hostname`
4. 一旦完成，通过右键单击文件资源管理器中的驱动器并选择 **Disconnect** 来断开连接。

#### 1.15 使用 rsync 维护源代码的本地副本

使用 SSHFS 访问远程文件的另一种方法是使用rsync将远程主机上文件夹的全部内容复制到本地计算机。rsync命令将确定每次运行时需要更新哪些文件，这比使用scp或sftp等工具要高效和方便得多。如果您确实需要使用多文件或性能密集型的本地工具，那么首先要考虑这一点。

rsync命令在macOS上是开箱即用的，可以使用Linux包管理器安装(例如sudo apt-get在Debian/Ubuntu上安装rsync)。对于Windows，您需要使用WSL或Cygwin来访问命令。

要使用该命令，导航到您想要存储同步内容的文件夹，并运行以下命令，将user@hostname替换为远程用户和主机名/ IP，将/remote/source/code/path替换为远程源代码位置。

macOS、Linux 或 WSL 内部：

```shell
rsync -rlptzv --progress --delete --exclude=.git "user@hostname:/remote/source/code/path" .
```

或在 Windows 命令提示符中使用 WSL：

```shell
wsl rsync -rlptzv --progress --delete --exclude=.git "user@hostname:/remote/source/code/path" "$(wslpath -a '%CD%')"
```

您可以在每次希望获得文件的最新副本时重新运行此命令，并且只传输更新。出于性能原因，特意排除了. Git文件夹，这样您就可以使用本地Git工具，而不用担心远程主机上的状态。

要推送内容，请反转命令中的源参数和目标参数。但是，在Windows上，您应该在项目中添加一个.gitattributes文件，以便在此之前强制执行一致的行结束符。有关详细信息，请参见解决Git行结束问题。

```shell
rsync -rlptzv --progress --delete --exclude=.git . "user@hostname:/remote/source/code/path"
```

#### 1.16 清理远程上的 Vs Code 服务器

SSH扩展提供了一个命令来清理远程机器上的 Vs Code 服务器，remote -SSH: Uninstall VS Code Server from Host…该命令做两件事:杀死所有正在运行的 Vs Code 服务器进程，并删除安装服务器的文件夹。

如果你想手动运行这些步骤，或者命令不适合你，你可以这样运行脚本：

```shell
kill -9 `ps ax | grep "remoteExtensionHostAgent.js" | grep -v grep | awk '{print $1}'`
kill -9 `ps ax | grep "watcherService" | grep -v grep | awk '{print $1}'`
rm -rf ~/.vscode-server # Or ~/.vscode-server-insiders
```

 Vs Code 服务器以前是在~/下安装的。vscode-remote，以便您也可以检查该位置。

### 2. 容器技巧

#### 2.1 Docker桌面的Windows提示

Windows的Docker桌面在大多数设置中都工作得很好，但是有一些“陷阱”可能会导致问题。下面是一些避免这些问题的建议:

共享驱动器时使用AD域帐户或本地管理员帐户。不要使用AAD(基于电子邮件的)帐户。AAD(基于电子邮件)帐户有众所周知的问题，如Docker第132期和第1352期中记录的那样。如果必须使用AAD帐户，请在您的计算机上创建一个单独的本地管理员帐户，仅用于共享驱动器。按照这篇博文中的步骤来设置一切。

坚持使用字母数字密码，以避免驱动器共享问题。当被要求在Windows上共享驱动器时，系统会提示您输入具有该计算机管理权限的帐户的用户名和密码。如果您被警告用户名或密码不正确，这可能是由于密码中的特殊字符。例如，!，[和]就会引起问题。将密码更改为要解析的字母数字字符。有关Docker卷安装问题的详细信息，请参阅此问题。

使用您的Docker ID登录到Docker(而不是您的电子邮件)。Docker CLI只支持使用您的Docker ID，因此使用电子邮件可能会导致问题。有关详细信息，请参见Docker第935期。

如果您仍然有问题，请参阅Docker桌面的Windows故障排除指南。

#### 2.2 在Docker桌面中启用文件共享

VS Code Remote - Containers扩展只能在代码位于与Docker共享的文件夹或驱动器中时自动将源代码挂载到容器中。如果您从非共享位置打开一个开发容器，容器将成功启动，但是工作区将是空的。

要更改Docker的驱动器和文件夹共享设置:

##### 2.2.1 窗口:

右键单击Docker任务栏项并选择Settings。
转到Shared Drives选项卡，检查源代码所在的驱动器。

##### 2.2.2 macOS:

单击Docker菜单栏项并选择Preferences。
转到文件共享选项卡。确认包含源代码的文件夹位于列出的共享文件夹之一之下。

#### 2.3解决容器中的Git行结束问题(导致许多修改文件)

由于Windows和Linux使用不同的默认行尾，Git可能会报告大量修改后的文件，这些文件除了行尾没有任何区别。为了防止这种情况发生，可以使用.gitattributes文件或在Windows端全局禁用行结束转换。

通常，在存储库中添加或修改.gitattributes文件是解决此问题的最可靠方法。将此文件提交到源代码控制将帮助其他人，并允许您根据存储库更改行为。例如，将以下内容添加到.gitattributes文件到存储库的根目录中，将强制所有内容为LF，但需要CRLF的Windows批处理文件除外：

```shell
* text=auto eol=lf
*.{cmd,[cC][mM][dD]} text eol=crlf
*.{bat,[bB][aA][tT]} text eol=crlf
```

注意，这在Git v2.10+中是有效的，所以如果遇到问题，请确保安装了最新的Git客户机。您可以将存储库中需要CRLF的其他文件类型添加到这个文件中。

如果您希望始终上传unix样式的行尾(LF)，可以使用input选项。

```shell
git config --global core.autocrlf input
```

如果您想完全禁用行结束对话，请运行以下命令：

```shell
git config --global core.autocrlf false
```

最后，您可能需要再次克隆存储库，以使这些设置生效。

#### 2.4 使用Docker组合时，避免在容器中设置Git

有关解决此问题的信息，请参阅主容器文章中与容器共享Git凭据。

#### 2.5 在从容器执行Git推送或同步时解决挂起问题

如果您使用SSH克隆Git存储库，并且您的SSH密钥具有密码，那么 Vs Code 的pull和sync特性在远程运行时可能会挂起。

要么使用没有密码的SSH密钥，要么使用HTTPS克隆，要么从命令行运行git push来解决这个问题。

#### 2.6 解决关于缺少Linux依赖项的错误

有些扩展依赖于某些Docker映像中没有的库。有关解决此问题的一些选项，请参阅容器文章。

#### 2.7 加速Docker桌面中的容器

默认情况下，Docker Desktop只提供容器计算机容量的一小部分。在大多数情况下，这已经足够了，但是如果您正在做一些需要更多容量的事情，您可以增加内存、CPU或磁盘的使用。

首先，尝试停止您不再使用的任何正在运行的容器。

如果这并不能解决您的问题，那么您可能想看看CPU使用情况是否是真正的问题，或者是否发生了其他事情。检查这一点的一个简单方法是安装资源监视器扩展。当安装在容器中时，它在状态栏中提供关于容器容量的信息。

![Resource Monitor extension](https://code.visualstudio.com/assets/docs/remote/troubleshooting/resource-monitor.png)

如果你想要一直安装这个扩展，把它添加到你的设置中。

```json
"remote.containers.defaultExtensions": [
    "mutantdino.resourcemonitor"
]
```

如果确定需要增加容器的机器容量，请遵循以下步骤:

右键单击Docker任务栏项并选择Settings / Preferences。
转到高级以增加CPU、内存或交换。
在Mac上，转到磁盘以增加机器上允许使用的磁盘Docker数量。在Windows上，这是位于高级与其他设置。
最后，如果容器是磁盘密集型的，那么应该避免使用本地文件系统的卷(绑定)挂载来存储数据文件(例如数据库数据文件)，特别是在Windows上。您还可以在Mac上使用缓存的挂载一致性，或者为源代码使用指定的卷。

#### 2.8 清理未使用的容器和图像

如果您看到Docker报告您的磁盘空间已用完的错误，通常可以通过清除未使用的容器和映像来解决这个问题。有几种方法可以做到这一点:

选项1:使用Docker扩展。

如果还没有安装Docker扩展，请从Extensions视图中安装Docker扩展。

注意:使用容器中打开的 Vs Code 窗口中的Docker扩展有一些限制。大多数容器都没有安装Docker命令行。因此，从Docker扩展调用的命令依赖于Docker命令行，例如Docker: Show Logs, fail。如果需要执行这些命令，请打开一个新的本地窗口，并从这个 Vs Code 窗口使用Docker扩展名，或者在容器中设置Docker。

然后，您可以转到Docker视图并展开容器或图像节点，右键单击并选择Remove Container / Image。
![container](https://code.visualstudio.com/assets/docs/remote/containers/docker-remove.png)
选项2:使用Docker CLI选择要删除的容器:

1. 打开本地终端/命令提示符(或者在 Vs Code 中使用本地窗口)。
2. 键入docker ps -a查看所有容器的列表。
3. 从该列表中键入 `docker rm <Container ID>` 以删除容器。
4. 键入docker image prune以删除任何未使用的图像。

如果docker ps没有提供足够的信息来标识要删除的容器，下面的命令将列出 Vs Code 管理的所有开发容器以及用于生成它们的文件夹。

```shell
docker ps -a --filter="label=vsch.quality" --format "table {{.ID}}\t{{.Status}}\t{{.Image}}\tvscode-{{.Label \"vsch.quality\"}}\t{{.Label \"vsch.local.folder\"}}"
```

选项3:使用Docker撰写:

打开本地终端/命令提示符(或者在 Vs Code 中使用本地窗口)。
转到docker-compose目录。yml文件。
键入docker- composition down来停止和删除容器。如果有多个Docker组合文件，可以使用-f参数指定其他Docker组合文件。
选项4:删除所有不运行的容器和图像:

打开本地终端/命令提示符(或者在 Vs Code 中使用本地窗口)。
输入docker system prune——all。

#### 2.9 解决Dockerfile构建失败的图像使用Debian 8

当构建使用基于Debian 8/Jessie的图像的容器时——例如老版本的节点:8图像——您可能会遇到以下错误：

```txt
...
W: Failed to fetch http://deb.debian.org/debian/dists/jessie-updates/InRelease  Unable to find expected entry 'main/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.
...
```

这是一个众所周知的问题，因为Debian 8被“归档”了。最新版本的映像通常通过升级到Debian 9/Stretch来解决这个问题。

有两种方法可以解决这个错误:

选项1:删除依赖于映像的任何容器，删除映像，然后再次尝试构建。这应该下载一个不受问题影响的更新图像。有关详细信息，请参见清除未使用的容器和图像。

选项2:如果不想删除容器或图像，请在apt或apt-get命令之前将这一行添加到Dockerfile中。它为Jessie添加了所需的源列表:

```shell
# Add archived sources to source list if base image uses Debian 8 / Jessie
RUN cat /etc/*-release | grep -q jessie && printf "deb http://archive.debian.org/debian/ jessie main\ndeb-src http://archive.debian.org/debian/ jessie main\ndeb http://security.debian.org jessie/updates main\ndeb-src http://security.debian.org jessie/updates main" > /etc/apt/sources.list
```

#### 2.10 在使用电子邮件时解决Docker集线器符号错误

Docker CLI只支持使用您的Docker ID，因此使用电子邮件登录可能会导致问题。有关详细信息，请参见Docker第935期。

作为一个解决方案，使用您的Docker ID登录到Docker，而不是您的电子邮件。

#### 2.11 Hyperkit在macOS上的高CPU利用率

已知的问题与Docker的Mac，可以驱动高CPU峰值。特别是，在查看文件和构建时出现高CPU使用率。如果您看到com.docker的CPU使用率很高。虽然开发容器中发生的事情很少，但是您可能会遇到这个问题。跟踪Docker问题以获得更新和修复。

#### 2.12 高级容器配置技巧

有关以下主题的信息，请参阅高级容器配置文章:

添加环境变量
添加另一个卷挂载
更改或删除默认的源代码挂载
向开发容器添加非根用户
提高容器磁盘性能
避免在容器重新构建时重新安装扩展
从容器中使用Docker或Kubernetes
同时连接到多个容器
在远程Docker机器或SSH主机上的容器内开发
减少Dockerfile构建警告

### 3. WSL的技巧

#### 3.1 选择远程WSL使用的默认分布

在非默认的WSL发行版上打开远程WSL窗口需要Windows 10, 2019年5月更新(1903版)。对于较老的WSL版本， Vs Code 将使用您的系统默认发行版。您可以根据需要使用wslconfig.exe更改默认值。

例如：

```shell
wslconfig /setdefault Ubuntu
```

你可以看到你已经安装了哪些发行版运行：

```shell
wslconfig /l
```

#### 3.2 Vs Code 服务器启动时挂起

如果有自定义启动脚本阻止启动，就会发生这种情况。

 Vs Code 服务器在交互式登录shell中启动，并使用已配置的shell。有关如何指定shell的更多信息，请参阅本文。

默认情况下，bash用作shell。Bash首先查找/etc/profile下的启动文件，然后查找~/下的任何启动文件。bash_profile、~ /。bash_login ~ / . profile。如果这个查找看起来没有必要，您可以在~/.bashrc中包含所有启动设置。检查这些文件是否包含任何可能阻止服务器启动的命令。例如，不建议使用启动脚本启动另一个shell。

#### 3.3 修复代码命令无法工作的问题

如果在窗口上从WSL终端键入代码不起作用，您可能会丢失WSL中路径中的一些关键位置。

通过打开WSL终端并键入echo $PATH进行检查。您应该看到以下列出的路径：

`/mnt/c/Windows/System32`

 Vs Code 安装路径。默认情况下，这应该是：

```shell
/mnt/c/Users/Your Username/AppData/Local/Programs/Microsoft VS Code/bin
```

但是，如果您安装了系统安装程序版本，安装路径是：

```shell
/mnt/c/Program Files/Microsoft VS Code/bin
```

...或者...

```shell
/mnt/c/Program Files (x86)/Microsoft VS Code/bin
```

如果缺少 Vs Code 安装路径，编辑您的.bashrc，添加以下内容，并启动一个新的终端:

```shell
WINDOWS_USERNAME="Your Username"
VSCODE_PATH="/mnt/c/Users/${WINDOWS_USERNAME}/AppData/Local/Programs/Microsoft VS Code/bin"
# or...
# VSCODE_PATH="/mnt/c/Program Files/Microsoft VS Code/bin"
# or...
# VSCODE_PATH="/mnt/c/Program Files (x86)/Microsoft VS Code/bin"

export PATH=$PATH:/mnt/c/Windows/System32:${VSCODE_PATH}
```

注意:请确保在目录名中引用或转义空格。

#### 3.4 解决关于丢失依赖项的错误

一些扩展依赖于某些WSL Linux发行版的普通安装中没有的库。您可以通过使用Linux发行版的包管理器向其添加额外的库。对于基于Ubuntu和Debian的发行版，运行sudo apt-get install 来安装所需的库。</package>查看有关扩展或运行时的文档，以了解更多安装细节。

#### 3.5 解决WSL中的Git行结束问题(导致许多修改文件)

由于Windows和Linux使用不同的默认行尾，Git可能会报告大量修改后的文件，这些文件除了行尾没有任何区别。为了防止这种情况发生，可以使用.gitattributes文件或在Windows端全局禁用行结束转换。

通常，在存储库中添加或修改.gitattributes文件是解决此问题的最可靠方法。将此文件提交到源代码控制将帮助其他人，并允许您根据存储库更改行为。例如，将以下内容添加到.gitattributes文件到存储库的根目录中，将强制所有内容为LF，但需要CRLF的Windows批处理文件除外:

```shell
* text=auto eol=lf
*.{cmd,[cC][mM][dD]} text eol=crlf
*.{bat,[bB][aA][tT]} text eol=crlf
```

注意，这在Git v2.10+中是有效的，所以如果遇到问题，请确保安装了最新的Git客户机。您可以将存储库中需要CRLF的其他文件类型添加到这个文件中。

如果您希望始终上传unix样式的行尾(LF)，可以使用input选项。

```shell
git config --global core.autocrlf input
```

如果您想完全禁用行结束对话，请运行以下命令:

```shell
git config --global core.autocrlf false
```

最后，您可能需要再次克隆存储库，以使这些设置生效。

#### 3.6 在从WSL执行Git推送或同步时解决挂起问题

如果您使用SSH克隆Git存储库，并且您的SSH密钥具有密码，那么 Vs Code 的pull和sync特性在远程运行时可能会挂起。

要么使用没有密码的SSH密钥，要么使用HTTPS克隆，要么从命令行运行git push来解决这个问题。

### 4. 扩展提示

虽然许多扩展可以不加修改地工作，但是有一些问题会阻止某些特性按预期工作。在某些情况下，可以使用另一个命令来解决这个问题，而在其他情况下，可能需要修改扩展名。本节为常见问题和解决这些问题的技巧提供快速参考。您还可以参考关于支持远程开发的主要扩展文章，以获得关于修改扩展以支持远程扩展主机的深入指南。

#### 4.1 远程应用时，本地绝对路径设置失败

当您连接到远程端点时，VS Code的本地用户设置将被重用。虽然这可以保持用户体验的一致性，但是您可能需要在本地机器和每个主机/容器/ WSL之间更改绝对路径设置，因为目标位置不同。

解决方案:在连接到远程端点后，可以通过运行Preferences: Open remote settings command from command Palette (F1)或在settings editor中选择remote选项卡来设置特定于端点的设置。这些设置将覆盖您在连接时的所有本地设置。

#### 4.2 需要在远程端点上安装本地VSIX

有时，您希望在远程机器上安装本地VSIX，无论是在开发期间还是在扩展作者要求您尝试修复时。

解决方案:一旦连接到SSH主机、容器或WSL，就可以像在本地一样安装VSIX。运行扩展:从VSIX安装…命令面板中的命令(F1)。您可能还想添加“扩展”。":错误的设置。json防止自动更新到最新的市场版本。有关在远程环境中开发和测试扩展的更多信息，请参见支持远程开发。

#### 4.3 浏览器不能在本地打开

一些扩展使用外部节点模块或自定义代码来启动浏览器窗口。不幸的是，这可能导致扩展远程而不是本地启动浏览器。

解决方案:扩展可以切换到使用vscode.env。openExternal API来解决这个问题。有关详细信息，请参阅扩展作者指南。

#### 4.4 剪贴板无法工作

一些扩展使用节点模块(如clipboard)与剪贴板集成。不幸的是，这可能导致扩展与远程端的剪贴板不正确地集成。

解决方案:扩展可以切换到 Vs Code 剪贴板API来解决问题。有关详细信息，请参阅扩展作者指南。

#### 4.5 无法从浏览器或应用程序访问本地web服务器

当在容器或SSH主机中工作时，浏览器所连接的端口可能被阻塞。

解决方案:扩展可以切换到vscode.env。openExternal API(它自动转发本地主机端口)来解决这个问题。有关详细信息，请参阅扩展作者指南。

#### 4.6 不显示WebView内容

如果扩展的WebView内容使用iframe连接到本地web服务器，则WebView连接的端口可能被阻塞。

解决方案:WebView API现在包含了一个portMapping属性，扩展可以使用它来解决这个问题。有关详细信息，请参阅扩展作者指南。

#### 4.7 阻塞本地主机端口

如果您试图从外部应用程序连接到本地主机端口，该端口可能被阻塞。

解决方案:目前还没有API用于通过编程方式转发任意端口的扩展，但是您可以使用远程容器:从容器转发端口……或远程ssh:从活动主机转发端口…手动操作。

#### 4.8 存储扩展数据的错误

扩展可以通过查找~/来尝试持久化全局数据。Linux上的配置/代码文件夹。这个文件夹可能不存在，这可能导致扩展抛出ENOENT这样的错误:没有这样的文件或目录，打开“/root/.config/Code/User/filename-go -here”。

解决方案:扩展可以使用上下文。globalStoragePath或上下文。属性来解决此问题。有关详细信息，请参阅扩展作者指南。

#### 4.9 每次连接到新端点时都不能登录/必须登录

需要登录的扩展可以使用它们自己的代码保存秘密。由于缺少依赖项，此代码可能会失败。即使成功了，秘密也将被远程存储，这意味着您必须为每个新端点登录。

解决方案:扩展可以使用keytar节点模块来解决这个问题。有关详细信息，请参阅扩展作者指南。

#### 4.10 不兼容的扩展阻止 Vs Code 连接

如果在远程主机、容器或WSL中安装了不兼容的扩展，我们就会看到 Vs Code 服务器由于不兼容而挂起或崩溃的实例。如果扩展立即激活，这将阻止您连接并卸载扩展。

解决方案:通过以下步骤手动删除远程扩展文件夹:

对于容器，请确保您的devcontainer。json不再包含对错误扩展的引用。

接下来，使用单独的终端/命令提示符连接到远程主机、容器或WSL。

如果是SSH或WSL，则相应地连接到环境(运行SSH连接到服务器或打开WSL终端)。
如果使用容器，请通过调用docker ps -a来标识容器ID，并在列表中查找具有正确名称的图像。如果容器被停止，运行`docker run -it <id> /bin/sh`。如果正在运行，运行 `docker exec - <id> /bin/sh`。
连接好后，运行rm -rf ~/。用于 Vs Code 稳定和/或rm -rf ~/的vscode-server/扩展。vscode-server-insider /扩展，用于 Vs Code 内部人员删除所有扩展。

#### 4.11 交付或获取预先构建的本机模块的扩展会失败

与 Vs Code 扩展绑定(或动态获取)的本机模块必须使用electronic的电子重建重新编译。然而，VS Code Server运行一个标准(非电子)版本的Node。，这可能导致二进制文件在远程使用时失败。

解决方案:需要修改扩展来解决这个问题。他们将需要包含(或动态获取)两套二进制文件(electronic和standard Node.js)，用于 Vs Code 附带的Node.js中的“模块”版本，然后检查上下文。executionContext = = = vscode.ExtensionExecutionContext。远程在它们的激活函数中设置正确的二进制文件。有关详细信息，请参阅扩展作者指南。

#### 4.12 扩展只在非x86_64主机或Alpine Linux上失败

如果扩展在Debian 9+、Ubuntu 16.04+或RHEL / CentOS 7+远程SSH主机、容器或WSL上工作，但在受支持的非x86_64主机(例如ARMv7l)或Alpine Linux容器上失败，则扩展可能只包含不支持这些平台的本地代码或运行时。例如，扩展可能只包含本地模块或运行时的x86_64编译版本。对于Alpine Linux，由于在Alpine Linux (musl)和其他发行版(glibc)中实现libc的方式存在根本差异，所包含的本地代码或运行时可能无法工作。

解决方案:扩展将需要选择通过编译/包括这些额外目标的二进制文件来支持这些平台。需要注意的是，一些第三方npm模块可能还包含可能导致此问题的本机代码。因此，在某些情况下，您可能需要使用npm模块作者来添加额外的编译目标。有关详细信息，请参阅扩展作者指南。

#### 4.13 扩展由于缺少模块而失败

依赖于electronic或 Vs Code 基模块(扩展API没有公开)的扩展在远程运行时可能会失败。您可能会在Developer Tools console中看到一些错误，比如没有找到original-fs。

解决方案:消除对电子模块的依赖，或者提供一个后备方案。有关详细信息，请参阅扩展作者指南。

#### 4.14 无法访问/传输远程工作区文件到本地计算机

在外部应用程序中打开工作区文件的扩展可能会遇到错误，因为外部应用程序不能直接访问远程文件。

解析:目前没有。我们正在研究扩展如何能够从远程工作区传输文件来解决这个问题。

#### 4.15 无法从扩展访问附加设备

访问本地附加设备的扩展在远程运行时将无法连接到它们。

解析:目前没有。我们正在研究解决这个问题的最佳方法。

### 5. 问题和反馈

参见远程开发常见问题。
堆栈溢出搜索。
添加特性请求或报告问题。
