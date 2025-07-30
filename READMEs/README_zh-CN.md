# ReZygisk

[Bahasa Indonesia](/READMEs/README_id-ID.md)|[Tiếng Việt](/READMEs/README_vi-VN.md)|[Português Brasileiro](/READMEs/README_pt-BR.md)|[French](/READMEs/README_fr-FR.md)|[日本語](/READMEs/README_ja-JP.md)|[简体中文](/READMEs/README_zh-CN.md)

ReZygisk是Zygisk Next的一个分支，是Zygisk的独立实现，为KernelSU、APatch和Magisk（官方和Kitsune）提供Zygisk API支持。

该项目旨在对代码库进行全面的现代化改造，并以C语言重新编写，实现对Zygisk API更加高效且快速的支持。同时，项目将采用更为宽松、更加符合自由开源软件（FOSS）原则的许可证。

## 为什么选择ReZygisk？

Zygisk Next的最新版本并非开源，相关代码完全由其开发者保留。这不仅限制了我们为该项目做出贡献，还使得代码无法被审查，这是一个重大的安全隐患，因为Zygisk Next是一个以超级用户（root）权限运行的模块，可以访问整个系统。

尽管Zygisk Next的开发者在Android社区中享有盛誉并广受信任，但这并不意味着其代码不存在恶意行为或安全漏洞。我们（PerformanC）理解他们有理由将代码保持闭源，但我们持相反观点。

## 优点

- FOSS (永久保持)

## 依赖项

| 工具          | 说明                               |
| ------------- | ---------------------------------- |
| `Android NDK` | Native Development Kit for Android |

### C++ 依赖项

| 依赖项     | 说明                        |
| ---------- | --------------------------- |
| `lsplt`    | Simple PLT Hook for Android |

## 安装

### 1. 选择正确的 ZIP 文件

选择构建/压缩包非常重要，因为它将决定ReZygisk的隐藏程度和稳定性。不过，这并不复杂：

- `release` 版本应该是大多数情况下的选择，它移除了应用层日志记录，并提供了更优化的二进制文件。
- `debug` 版本则恰恰相反，它包含大量日志记录且未进行优化。因此，仅建议**在调试过程中使用该版本**，或**在提交Issue时用于获取相关日志**。

关于分支，除非开发者另有说明，或者您希望测试即将发布的新功能且已了解相关风险，否则应始终使用`主分支（main branch）`。

### 2. 刷入ZIP文件

在选择了正确的构建后，需要使用您当前的root管理器（如Magisk或KernelSU）刷入ZIP文件。您可以通过在root管理器的`模块`部分选择已下载的ZIP文件来完成此操作。

刷入完成后，请检查安装日志，确保没有错误。如果一切正常，即可重启设备。

> [!WARNING]
> Magisk用户应禁用内置的Zygisk，因为它将与ReZygisk冲突。这可以通过进入Magisk的`设置`部分并禁用`Zygisk`选项来完成。

### 3. 验证安装

重启后，您可以通过检查root管理器的`模块`部分的模块描述来验证ReZygisk是否正常工作，描述会显示必要的守护进程运行状态。例如，如果您的环境同时支持64位和32位，它应该看起来类似于： `[monitor: 😋 tracing, zygote64: 😋 injected, daemon64: 😋 running (...) zygote32: 😋 injected, daemon32: 😋 running (...)] Standalone implementation of Zygisk.`

## 翻译

目前有两种不同的方式可以为ReZygisk提供翻译：

- 对于README的翻译，您可以在`READMEs`文件夹中创建一个新文件，遵循`README_<language>.md`的命名规范，其中`<language>`是语言代码（例如，`README_pt-BR.md`代表巴西葡萄牙语），并将你的修改通过Pull Request提交到`main`分支。
- 对于ReZygisk WebUI的翻译，你应该首先在我们的Crowdin上进行贡献。审核通过后，请从Crowdin获取`.json`文件，并提交包含您修改内容的Pull Request——将`.json`文件添加到`webroot/lang`文件夹，并按照字母顺序将您的译者信息添加至`TRANSLATOR.md`文件中。

## 支持

对于任何与ReZygisk或其他PerformanC项目相关的问题，欢迎加入以下任意频道：

- Discord频道：[PerformanC](https://discord.gg/uPveNfTuCJ)
- ReZygisk Telegram频道：[@rezygisk](https://t.me/rezygisk)
- PerformanC Telegram频道：[@performancorg](https://t.me/performancorg)
- PerformanC Signal群组：[@performanc](https://signal.group/#CjQKID3SS8N5y4lXj3VjjGxVJnzNsTIuaYZjj3i8UhipAS0gEhAedxPjT5WjbOs6FUuXptcT)

## 贡献

在向ReZygisk提供贡献时，必须遵守PerformanC的[贡献指南](https://github.com/PerformanC/contributing)，包括其安全政策、行为准则及代码规范。

## 许可证

ReZygisk主要由Dr-TSNG以GPL许可证授权，但也由PerformanC组织以AGPL 3.0许可证授权重写的代码。更多信息请参阅[开放源代码组织（Open Source Initiative）](https://opensource.org/licenses/AGPL-3.0)。