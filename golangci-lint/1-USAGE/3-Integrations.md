# 集成（Integrations）

## 编辑器集成

### [Go for Visual Studio Code.](https://marketplace.visualstudio.com/items?itemName=golang.Go)

VS Code 的推荐设置是：

```json
"go.lintTool": "golangci-lint",
"go.lintFlags": [
  "--fast"
]
```

如果你在编辑器中使用 `golangci-lint` 但没有加上 `--fast` 参数，那么这个工具可能会占用大量计算资源导致编辑器出现卡顿、冻结等问题。Golangci-lint 会自动发现 `.golangci.yml` 配置文件：您无需在 VS Code 设置中配置它。

### Sublime Text

SublimeLinter 有相应的[插件](https://github.com/SublimeLinter/SublimeLinter-golangcilint)。

### GoLand

如何配置：

+ 安装[插件](https://plugins.jetbrains.com/plugin/12496-go-linter)
+ 使用现有的 `golangci-lint` 模板添加 [File Watcher](https://www.jetbrains.com/help/go/settings-tools-file-watchers.html)。
+ 如果您的 GoLand 版本没有 `golangci-lint` [File Watcher](https://www.jetbrains.com/help/go/settings-tools-file-watchers.html) 模板，您可以配置自己的模板并使用参数运行 `--disable=typecheck $FileDir$`。

### GNU Emacs

插件如下：

+ [Spacemacs](https://github.com/syl20bnr/spacemacs/blob/develop/layers/+lang/go/README.org#linting)
+ [flycheck checker.](https://github.com/weijiangan/flycheck-golangci-lint)

### Vim

以下插件支持 `golangci-lint`：

+ [vim-go;](https://github.com/fatih/vim-go)
+ [ALE;](https://github.com/dense-analysis/ale)
+ [Syntastic.](https://github.com/vim-syntastic/syntastic)

### Atom

[go-plus](https://github.blog/2022-06-08-sunsetting-atom/) 支持 golangci-lint.

## Shell 自动补全

`golangci-lint` 可以生成 bash、fish、powershell 和 zsh 补全文件。

### macOS

`bash-completion` 有两个版本，v1 和 v2。V1 适用于 Bash 3.2（这是 macOS 上的默认设置），v2 适用于 Bash 4.1+。`golangci-lint` 补全脚本在 bash-completion v1 和 Bash 3.2 无法正常工作。它需要 bash-completion v2 和 Bash 4.1+。因此，为了能够在 macOS 上正确使用 golangci-lint 补全，您必须安装和使用 Bash 4.1+（[说明](https://itnext.io/upgrading-bash-on-macos-7138bd1066ba?gi=edc61b56c400)）。以下说明假定您使用 Bash 4.1+（即任何 4.1 或更高版本的 Bash）。

安装 `bash-completion v2`：

```bash
brew install bash-completion@2
echo 'export BASH_COMPLETION_COMPAT_DIR="/usr/local/etc/bash_completion.d"' >>~/.bashrc
echo '[[ -r "/usr/local/etc/profile.d/bash_completion.sh" ]] && . "/usr/local/etc/profile.d/bash_completion.sh"' >>~/.bashrc
exec bash # reload and replace (if it was updated) shell
type _init_completion && echo "completion is OK" # verify that bash-completion v2 is correctly installed
```

添加 `golangci-lint` bash 补全：

```bash
echo 'source <(golangci-lint completion bash)' >>~/.bashrc
source ~/.bashrc
```

### Linux

参阅有关 `golangci-lint completion <YOUR_SHELL> --help` 说明（将 `<YOUR_SHELL>` 替换为您喜欢的）。

## CI 整合（Integration）

查看我们的 [Github Action](./1-Install.md#github-actions)。