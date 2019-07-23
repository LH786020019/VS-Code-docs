<!--
 * @Author: haoluo
 * @Date: 2019-07-23 09:06:37
 * @LastEditors: haoluo
 * @LastEditTime: 2019-07-23 11:19:57
 * @Description: file Network
 -->
## Visual Studio Code 上的网络连接
Visual Studio Code 构建在 [Electron](https://electron.atom.io/) 之上，并受益于 [Chromium](https://www.chromium.org/) 的所有网络堆栈功能。这也意味着 VS Code 用户可以获得 [Google Chrome](https://www.google.com/chrome/index.html) 中的大部分网络支持。

### 1. 常见的主机名
VS Code 中的一些功能需要网络通信才能工作，比如自动更新机制、查询和安装扩展以及遥测技术(telemetry)。要使这些特性在代理环境中正常工作，必须正确配置产品。

如果你在防火墙后面，需要允许 VS Code 使用特定的域，下面是你应该允许通信通过的主机名列表：
- `update.code.visualstudio.com`
- `code.visualstudio.com`
- `go.microsoft.com`
- `vscode.blob.core.windows.net`
- `marketplace.visualstudio.com`
- `*.gallerycdn.vsassets.io`
- `rink.hockeyapp.net`
- `vscode.search.windows.net`
- `raw.githubusercontent.com`
- `vsmarketplacebadge.apphb.com`

### 2. 代理服务器支持
VS Code 与 Google Chromium 具有完全相同的代理服务器支持。下面是 [Chromium 文档](https://www.chromium.org/developers/design-documents/network-settings)的一个片段：
```md
" Chromium 网络堆栈使用系统网络设置，以便用户和管理员能够轻松地控制所有应用程序的网络设置。网络设置包括：
 - proxy settings
 - SSL/TLS settings
 - certificate revocation check settings
 - certificate and private key stores"
```
这意味着您的代理设置应该被自动拾取。

否则，您可以使用以下命令行参数来控制您的代理设置：
```shell
# Disable proxy
--no-proxy-server

# Manual proxy address
--proxy-server=<scheme>=<uri>[:<port>][;...] | <uri>[:<port>] | "direct://"

# Manual PAC address
--proxy-pac-url=<pac-file-url>

# Disable proxy per host
--proxy-bypass-list=(<trailing_domain>|<ip-address>)[:<port>][;...]
```

点击[此处](https://www.chromium.org/developers/design-documents/network-settings)了解有关这些命令行参数的更多信息。

#### 2.1 认证代理
通过身份验证的代理应该在添加了 [PR #22369](https://github.com/Microsoft/vscode/pull/22369) 的 VS Code 中无缝工作。

支持的认证方法有：
- Basic
- Digest
- NTLM
- Negotiate

当使用经过身份验证的 HTTP 代理背后的 VS Code 时，应该会出现以下身份验证弹出框：
![](https://code.visualstudio.com/assets/docs/setup/network/proxy.png "")

注意，SOCKS5 代理身份验证支持尚未实现；您可以[在 Chromium 的问题跟踪器](https://bugs.chromium.org/p/chromium/issues/detail?id=256785)中跟踪该问题。

点击[这里]https://www.chromium.org/developers/design-documents/http-authentication()阅读更多关于 VS Code 中的 HTTP 代理身份验证的信息。

#### 2.2 SSL 证书
HTTPS 代理经常重写传入请求的 SSL 证书。Chromium 的设计目的是拒绝由它不信任的证书签名的响应。如果您遇到任何 SSL 信任问题，有几个选项可供您选择：
- 由于 Chromium 只是使用 OS 的证书信任基础设施，所以首选的选项是将代理的证书添加到 OS 的信任链中。单击[这里](https://www.chromium.org/Home/chromium-security/root-ca-policy)阅读有关 Chromium 中的根证书策略的更多信息。
- 如果您的代理在 `localhost` 中运行，您总是可以尝试 [--allow-insecure-localhost](https://peter.sh/experiments/chromium-command-line-switches/#allow-insecure-localhost) 命令行标志。
- 如果其他方法都失败了，可以使用 [--ignore-certificate-errors](https://peter.sh/experiments/chromium-command-line-switches/#ignore-certificate-errors) 命令行标志告诉 VS Code 忽略所有证书错误。警告：这是危险的，不建议这样做，因为这会导致安全问题。

### 3. 遗留代理服务器支持
扩展还不能从 VS Code 所支持的代理支持中获益。您可以在 [GitHub](https://github.com/Microsoft/vscode/issues/12588) 中跟踪这个问题的发展。

与扩展类似，其他一些 VS Code 特性还不完全支持代理网络，即 CLI 接口。CLI 接口是您在命令提示符或终端运行 `code --install-extension vscodevim.vim` 时得到的。您可以在 [GitHub](https://github.com/Microsoft/vscode/issues/29910) 中跟踪这个问题的发展。

由于这两个限制，`http.proxy`、`http.proxyStrictSSL` 和 `http.proxyAuthorization` 变量仍然是 VS Code 设置的一部分，但是它们只在这两种场景中起作用。

### 4. 故障排除
下面是一些有用的链接，可以帮助你解决 VS Code 中的网络问题：
- [网络设置](https://www.chromium.org/developers/design-documents/network-settings)
- [调试使用网络代理的问题](https://www.chromium.org/developers/design-documents/network-stack/debugging-net-proxy)
- [在 Chrome 中配置 SOCKS 代理服务器](https://www.chromium.org/developers/design-documents/network-stack/socks-proxy)
- [代理设置和回退(Windows)](https://www.chromium.org/developers/design-documents/network-stack/proxy-settings-fallback)