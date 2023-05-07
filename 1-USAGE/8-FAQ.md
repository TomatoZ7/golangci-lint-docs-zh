# 常见问题（FAQ）

## 如何添加自定义 linter？

你可以自己集成它，请参阅[手册](https://golangci-lint.run/contributing/new-linters/)。或者你可以创建一个 [GitHub Issue](https://github.com/golangci/golangci-lint/issues/new)，我们将在时间允许时进行整合。

## 如何将 `golangci-lint` 集成到有数千个问题的大型项目中？

我们坚信每个项目都能够简单地集成 `golangci-lint`，即便这个项目很大。方法就是不去修复所有已存在的问题。只修复新增的问题：新代码产生的问题。为此，可以设置 CI 的 `--new-from-rev=HEAD~1` 选项来运行 `golangci-lint`。另外，查看 `--new` 选项，考虑到 CI 脚本生成的未暂存的文件会让 `--new` 只支出这些文件中的错误而不是最后一次 commit 存在的问题。在这方面 `--new-from-rev=HEAD~1` 更安全。通过这样做，您不会在代码中产生新问题，并且可以选择修复现有问题（或不修复）。

## 如何在 CI 中使用 `golangci-lint`

在 CI 中运行 golangci-lint 并检查其返回 code（exit code）。如果不是非零值，那么则意味着它检测到了一些问题或错误，构建失败。

参阅[如何在CI中正确安装 golangci-lint](./1-Install.md#ci-安装)

## 支持哪些 Go 版本

与 Go 团队相同（最后 2 个小版本）

从 golangci-lint v1.45.0 开始，官方支持 go1.18+，但有一些[限制](https://github.com/golangci/golangci-lint/issues/2649)。

## golangci-lint 无法运行

1. 请确保您使用的是最新的二进制版本。
2. 使用 `-v` 选项运行它并检查输出。
3. 如果以上都没有帮助，可以创建一个 [GitHub issue](https://github.com/golangci/golangci-lint/issues/new) 携带输出错误和上面的第 2 点。

## 为什么在第一次运行时使用 `--fast` 运行很慢

因为第一次运行会缓存类型信息。所有后续运行都将很快。通常这个选项在本地机器上的开发过程中使用，编译已经执行。