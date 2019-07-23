<!--
 * @Author: haoluo
 * @Date: 2019-07-23 09:06:21
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-23 10:58:34
 * @Description: file content
 -->
## Linux 上的 Visual Studio Code

### 1. 安装

#### 1.1 Snap
Visual Studio Code 在 [Snap Store](https://snapcraft.io/store) 中以 Snap 包的形式正式发布：
[![Snap](https://code.visualstudio.com/assets/docs/setup/linux/snap-store.png "Snap Store")](https://snapcraft.io/code)

你可以运行下面的命令简单地安装它：
```shell
sudo snap install --classic code # or code-insiders
```
安装完成后，Snap 守护进程将自动更新后台的 VS Code。每当有新的更新可用时，您将收到一个产品内更新通知。

< 注意：如果 `snap` 在您的 Linux 发行版中不可用，请检查下面的[安装 snapd 指南](https://docs.snapcraft.io/installing-snapd)，它可以帮助您进行设置。

从[官方 Snap 文档](https://docs.snapcraft.io/)了解更多关于 snaps 的信息。

#### 1.2 基于 Debian 和 Ubuntu 的发行版
安装基于 Debian/Ubuntu 发行版的 Visual Studio Code 的最简单方法是下载并安装 [.deb 包(64位)](https://go.microsoft.com/fwlink/?LinkID=760868)，如果有的话，可以通过图形软件中心，或者通过命令行：
```shell
sudo apt install ./<file>.deb

# 如果您使用的是较老的 Linux 发行版，则需要运行以下命令：
# sudo dpkg -i <file>.deb
# sudo apt-get install -f # Install dependencies
```
安装 `.deb` 包将自动安装 apt 存储库和签名密钥，以便使用系统的包管理器实现自动更新。注意，`32 位`和 `.tar.gz` 二进制文件也可以从 [VS Code 下载页面](https://code.visualstudio.com/Download)获得。

库和密钥也可以用以下脚本手动安装：
```shell
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
```

然后更新包缓存并使用以下命令安装包：
```shell
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install code # or code-insiders
```

#### 1.3 基于 RHEL、Fedora 和 CentOS 的发行版
我们目前在 `yum` 存储库中发布稳定的 64 位 VS Code，下面的脚本将安装密钥和库：
```shell
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
```

然后使用 `dnf` 更新包缓存并安装包(Fedora 22及以上)：
```shell
dnf check-update
sudo dnf install code
```
或者旧版本使用 `yum`：
```shell
yum check-update
sudo yum install code
```
由于手工签名过程和我们用来发布的系统，yum 存储库可能会落后，无法立即获得 VS Code 的最新版本。

#### 1.4 基于 openSUSE 和 SLE 的发行版
上面的 `yum` 存储库也适用于基于 openSUSE 和 SLE 的系统，下面的脚本将安装密钥和存储库：
```shell
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/vscode.repo'
```
然后使用以下命令更新包缓存并安装包：
```shell
sudo zypper refresh
sudo zypper install code
```
#### 1.5 用于 Arch Linux 的 AUR 包
这里有一个社区维护[用于 VS Code 的 Arch 用户存储库包](https://aur.archlinux.org/packages/visual-studio-code-bin)。

要从 `AUR` 获得更多关于安装的信息，请参考以下 wiki 条目：[安装 AUR 包](https://wiki.archlinux.org/index.php/Arch_User_Repository#Build_and_install_the_package)。

#### 1.6 用于 NixOS 的 Nix 包(或使用 Nix 包管理器的任何 Linux 发行版)
在 `nixpkgs` 存储库中有一个社区维护的 [VS Code Nix 包](https://github.com/NixOS/nixpkgs/blob/master/pkgs/applications/editors/vscode/default.nix)。要使用 `Nix` 安装它，请在您的 `config.nix` 中将 `allowUnfree` 选项设置为 `true`，然后执行：
```shell
nix-env -i vscode
```

#### 1.7 手动安装 .rpm 包
还可以手动下载和安装 [VS Code .rpm 包(64位)](https://go.microsoft.com/fwlink/?LinkID=760867)，但是除非安装了上面的存储库，否则自动更新将无法工作。一旦下载，它可以安装使用您的包管理器，例如使用 `dnf`：
```shell
sudo dnf install <file>.rpm
```
注意，32 位和 .tar.gz 二进制文件也可以从 [VS Code 下载页面](https://code.visualstudio.com/Download)获得。

### 2. 更新
VS Code 每月发布一次，您可以通过检查[发布说明](https://code.visualstudio.com/updates)来查看新版本何时可用。如果正确安装了 VS Code 存储库，那么您的系统包管理器应该像系统上的其他包一样处理自动更新。

注意:更新是自动的，并且在 [Snap 包](https://code.visualstudio.com/docs/setup/linux#_snap)的后台运行。

### 3. Node.js
`Node.js` 是一个流行的平台和运行时，可以轻松地构建和运行 JavaScript 应用程序。它还包括 [npm](https://www.npmjs.com/)，一个用于 `Node.js` 模块的包管理器。您将在我们的文档中经常看到 Node.js 和 npm，一些可选的 VS Code 工具需要 Node.js (例如 VS Code [扩展生成器](https://code.visualstudio.com/api/get-started/your-first-extension))。

如果您想在 Linux 上安装 Node.js，请参阅[通过 package manager 安装 Node.js](https://nodejs.org/en/download/package-manager)，以找到适合您的 Linux 发行版的 Node.js 包和安装说明。还可以使用 [Node 版本管理器](https://github.com/creationix/nvm)安装和支持 Node.js 的多个版本。

了解有关 JavaScript 和 Node.js 的更多信息，参见我们的 [Node.js 教程](https://code.visualstudio.com/docs/nodejs/nodejs-tutorial)，在这里您将学习如何使用 VS Code 运行和调试 Node.js 应用程序。

### 4. 将 VS Code 设置为默认文本编辑器

#### 4.1 xdg-open
您可以使用以下命令为 `xdg-open` 使用的文本文件( `文本(text)/纯文本(plain)` )设置默认文本编辑器：
```shell
xdg-mime default code.desktop text/plain
```

#### 4.2 Debian alternatives 系统
基于 Debian 的发行版允许使用 [Debian alternatives 系统](https://wiki.debian.org/DebianAlternatives)设置**默认编辑器**，而无需考虑 MIME 类型。您可以通过运行以下命令并选择 code 来设置：
```shell
sudo update-alternatives --set editor /usr/bin/code
```

### 5. 下一步
一旦你安装了 VS Code，这些主题将帮助你了解更多：
- [额外组件](https://love2.io/@LH786020019/doc/VS-Code-docs/setup/addi_comp.md) —— 学习如何安装 `Git`、`Node.js`、`TypeScript` 和类似 `Yeoman` 的工具。
- [用户界面](https://love2.io/@LH786020019/doc/VS-Code-docs/get_started/user_interface.md) —— VS Code 的快速定位。
- [用户/工作区设置](https://love2.io/@LH786020019/doc/VS-Code-docs/get_started/settings.md) —— 学习如何通过 settings 配置 VS Code 到您的首选项。

### 6. 常见问题

#### 6.1 Azure VM 问题
我得到一个 `“Running without the SUID sandbox”` 错误?

您可以安全地忽略这个错误。

#### 6.2 Debian 和移动文件到 trash
如果在 Debian 操作系统上从 VS Code Explorer 中删除文件时出现错误，可能是因为 VS Code 使用的 trash 实现不存在。

运行这些命令来解决这个问题：
```shell
sudo apt-get install gvfs-bin
```

#### 6.3 “Visual Studio Code 无法在这个大工作区中查看文件更改”(error ENOSPC))
当您看到这个通知时，它表明 VS Code 文件监视程序正在耗尽句柄，因为工作区很大并且包含许多文件。当前的限制可以通过运行：
```shell
cat /proc/sys/fs/inotify/max_user_watches
```
通过编辑 `/etc/sysctl.conf` 并将下面这一行添加到文件末尾，可以将这个限制增加到最大：
```shell
fs.inotify.max_user_watches=524288
```
然后可以通过运行 `sudo sysctl -p` 加载新值。注意，[Arch Linux](https://www.archlinux.org/) 的工作方式略有不同，详情请参阅[增加 inotify 观察者的数量](https://github.com/guard/listen/wiki/Increasing-the-amount-of-inotify-watchers)。

虽然 524288 是可以监视的最大文件数量，但是如果您所处的环境内存特别有限，您可能希望降低这个数字。每个文件表[占用 540 字节(32位) 或 ~1kB(64位)](https://stackoverflow.com/a/7091897/1156119)，因此假设所有 524288 个表都被使用了，那么上限大约为 256MB(32位) 或 512MB(64位)。

另一个选项是使用 `files.watcherExclude` [设置](https://love2.io/@LH786020019/doc/VS-Code-docs/get_started/settings.md)来从 VS Code 文件监视程序中排除特定的工作区目录。`files.watcherExclude`的默认值排除了 `node_modules` 和 `.git` 下的一些文件夹，但是您可以添加您不希望 VS Code 跟踪的其他目录。
```json
"files.watcherExclude": {
    "**/.git/objects/**": true,
    "**/.git/subtree-cache/**": true,
    "**/node_modules/*/**": true
  }
```

#### 6.4 我在 Ubuntu 里看不到中文
我们正在解决这个问题。同时，打开应用程序菜单，然后选择 `File > Preferences > Settings`。在 `Text Editor > Font` 部分，将 `“Font Family”` 设置为 `Droid Sans Mono, Droid Sans Fallback`。如果您想直接地编辑 `settings.json` 文件，如下所示设置 `editor.fontFamily`：
```json
    "editor.fontFamily": "Droid Sans Mono, Droid Sans Fallback"
```

#### 6.5 未安装 git 包
此错误可能在安装期间出现，通常由包管理器的列表过期引起。尝试更新并重新安装：
```shell
# For .deb
sudo apt-get update

# For .rpm (Fedora 21 and below)
sudo yum update

# For .rpm (Fedora 22 and above)
sudo dnf update
```

#### 6.6 在 Ubuntu 中 code bin 命令不会将窗口带到前台
在 Ubuntu 上，当 VS Code 已经在当前目录中打开时，运行 `code .`，不会将 VS Code 带到前台。这是操作系统的一个特性，可以使用 `ccsm` 禁用。
```shell
# Install
sudo apt-get update
sudo apt-get install compizconfig-settings-manager

# Run
ccsm
```
在 `General > General Options > Focus & Raise Behaviour`，设置 `“Focus Prevention Level”` 为 `“Off”`。请记住，这是一个 OS 级别的设置，适用于所有应用程序，而不仅仅是 VS Code。

#### 6.7 由于 "/etc/apt/sources.list.d/vscode.list: No such file or directory"，无法安装 .deb 包
当 `sources.list.d` 不存在或您无权创建该文件时可能会发生这种情况。要解决这个问题，请尝试手动创建文件夹和一个空的 `vscode.list` 文件：
```shell
sudo mkdir /etc/apt/sources.list.d
sudo touch /etc/apt/sources.list.d/vscode.list
```

#### 6.8 无法在 X 转发一个远程窗口时移动或调整窗口大小
如果您使用 X 转发来远程使用 VS Code ，您将需要使用本机标题栏来确保您可以正确地操作窗口。您可以通过设置 `window.titleBarStyle` 为 `native` 切换来使用它。

#### 6.9 使用自定义标题栏
Linux 上的自定义标题栏和菜单在默认情况下启用了几个月。自定义标题栏在 Windows 上取得了成功，但在 Linux 上的客户响应却表明情况并非如此。根据反馈，我们决定在Linux 上进行这个设置选项，并将本机标题栏保留为缺省值。

自定义标题栏提供了许多好处，包括强大的主题支持和通过键盘导航和屏幕阅读器更好的可访问性。不幸的是，这些优点并没有很好地应用到 Linux 平台上。Linux 有各种桌面环境和窗口管理器，可以让 VS Code 主题看起来与用户无关。对于需要改进易访问性的用户，我们建议在使用屏幕阅读器以易访问性模式运行时启用自定义标题栏。您仍然可以使用 `Window: Title Bar Style (window.titleBarStyle)` 设置手动设置标题栏。

#### 6.10 在编辑器中损坏光标，并启用了显示缩放功能
由于上游[问题 #14787](https://github.com/electron/electron/issues/14787) 与 Electron，鼠标光标可能呈现不正确的缩放启用。如果您注意到通常的文本光标没有像您预期的那样在编辑器中呈现，可以通过配置设置 `window.titleBarStyle` 为 `native` 尝试返回到本机菜单栏。

#### 6.11 Repository 更改了它的原始值
如果你收到类似以下的错误：
```shell
E: Repository '...' changed its 'Origin' value from '...' to '...'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
```
使用 `apt` 而不是 `apt-get`，您将会被提示接受原始地更改：
```shell
sudo apt update
```