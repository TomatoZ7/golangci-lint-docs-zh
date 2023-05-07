# 表现（Perforence）

## 内存使用

内存使用和执行时间之间的权衡可以通过 `GOGC` 环境变量来控制。更少的 GOGC 会导致更频繁地触发垃圾回收，golangci-lint 消耗更少的内存和更多的 CPU。下面是在这个仓库上运行的权衡表：

| `GOGC` | Peak Memory, GB | Execution Time, s |
| :---: | :---: | :---: |
| `5` | 1.1 | 60 |
| `10` | 1.1 | 34 |
| `20` | 1.3 | 25 |
| `30` | 1.6 | 20.2 |
| `50` | 2.0 | 17.1 |
| `80` | 2.2 | 14.1 |
| `100`（默认值） | 2.2 | 13.8 |
| off | 3.2 | 9.3 |

## 为什么 `golangci-lint` 这么快？

1. 工作共享

在运行过程中，`golangci-lint` 在特定的 linters（如 `golint`、`govet` 等）之间共享工作。我们不会交叉调用特定的 linter，而是使用它的 API。 对于中小型项目，linters 之间 50-90% 的工作可以重用。

+ 通过 `go/package` 只加载一次 `[]*packages.Package`

我们只为所有 linter 加载一次程序（解析所有文件和类型检查）。对于大多数 linters 来说，这是最繁重的操作：在 8 kLoC（kilo lines of code）的代码库上需要花费 5s，在 `$GOROOT/src` 需要花费 11s。

+ 只构建一次 `ssa.Program`

有些 linter（megacheck, interfacer, unparam）工作在 SSA representation 上。在 8kLoC 的代码库构建 representation 需要 1.5s，在 `$GOROOT/src` 上需要 6s。

+ 只解析源码和构建 AST（抽象语法树） 一次

解析一个源文件平均耗时 200us。解析 `$GOROOT/src` 所有的文件耗时 2s。目前我们解析每个文件不止一次，因为这并不是性能瓶颈。但是我们已经节省了很多额外的解析。我们计划只解析每个文件一次。

+ 只遍历一次文件和目录

在 `$GOROOT/src` 上会耗时 300 - 1000ms。

2. linters 智能调度

我们通过一种特殊的算法来调度 linters，该算法会将预计执行时间考虑在内。当启用其中一个重型 linters（megacheck 等）时，它可以节省 10-30% 的时间。

3. 不要交叉执行 shell 命令

所有 linters 的版本都由 go modules 固定，它们是内置的，你不需要单独安装它们。