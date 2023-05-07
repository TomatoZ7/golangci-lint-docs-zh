# 误报（False Positives）

误报是不可避免的，但是我们尽最大努力减少误报的数量。例如，我们有一组默认启用的[排除模式](./5-Configuration.md#命令行选项)。

如果出现误报，您有多种选择。

## 排除特定的 linter

大多数 linter 都有一份配置，有时误报可能与 linter 的错误配置有关。 所以建议检查 linters 配置。

除此之外，一些 linters 有专门的配置来排除或禁用规则。

这是一个关于 `staticcheck` 的例子：

```yaml
linters-settings:
  staticcheck:
    checks:
      - all
      - '-SA1000' # disable the rule SA1000
      - '-SA1004' # disable the rule SA1004
```

## 排除或跳过

### 按文本排除问题

按文本排除问题可以使用命令行选项 `-e` 或配置项 `issues.exclude`。当您决定忽略所有此类问题时，它会很有帮助。此外，您可以使用 `issues.exclude-rules` 配置项来为每个路径或每个 linter 进行配置。

在下面的示例中，所有包含 `exclude` 定义的语句的报告都会被排除：

```yaml
issues:
  exclude:
    - "Error return value of .((os\\.)?std(out|err)\\..*|.*Close|.*Flush|os\\.Remove(All)?|.*printf?|os\\.(Un)?Setenv). is not checked"
    - "exported (type|method|function) (.+) should have comment or be unexported"
    - "ST1000: at least one file in a package should have a package comment"
```

在下面的示例中，所有来自 `linters` 标注的 linters 的报告，并且包含 `text` 标注的文本都会被排除：

```yaml
issues:
  exclude-rules:
    - linters:
        - gomnd
      text: "mnd: Magic number: 9"
```

在下面的示例中，所有位于 `path` 标注的路径上并且包含 `text` 标注的文本的报告都会被排除：

```yaml
issues:
  exclude-rules:
    - path: path/to/a/file.go
      text: "string `example` has (\\d+) occurrences, make it a constant"
```

### 按路径排除问题

按路径排除问题可以通过 `run.skip-dirs`，`run.skip-files` 或者 `issues.exclude-rules` 配置项实现。

请注意，此处匹配的路径是相对于当前工作目录的。当配置包含检查特定目录的路径模式时，`--path-prefix` 参数可用于在匹配之前扩展路径。

在下面的示例中，所有来自 `linters` 标注的 linters，并且跟 `path` 标注的路径相关的报告都会被排除。

```yaml
issues:
  exclude-rules:
    - path: '(.+)_test\.go'
      linters:
        - funlen
        - goconst
```

在下面的示例中，`skip-files` 指定的相对路径的文件产生的报告都会被排除。

```yaml
run:
  skip-files:
    - path/to/a/file.go
```

在下面的示例中，`skip-dirs` 指定的相对路径目录下产生的报告都会被排除。

## Nolint 指令

要从所有 linters 排除问题，可以使用 `//nolint:all`。例如，如果它是在行内使用（不是从行的开头开始），那么它就会排除该行的问题。

```go
var bad_name int //nolint:all
```

指定的 linters 排除问题：

```go
var bad_name int //nolint:golint,unused
```

要排除代码块的问题，可以在首行使用该指令：

```go
//nolint:all
func allIssuesInThisFunctionAreExcluded() *string {
  // ...
}

//nolint:govet
var (
  a int
  b int
)
```

当然，你也可以排除某个文件的所有问题：

```go
//nolint:unparam
package pkg
```

可以在同一行内添加注释来解释或证明为什么使用 `//nolint`：

```go
//nolint:gocyclo // This legacy function is complex but the team too busy to simplify it
func someLegacyFunction() *string {
  // ...
}
```

你可以查看更多使用 `//nolint` 的案例在[我们的测试代码](https://github.com/golangci/golangci-lint/tree/master/pkg/result/processors/testdata)中。

使用 `//nolint` 而不是 `// nolint`，因为根据 Go 约定，机器可读的注释应该没有空格。

## 默认排除

一些排除被认为是常见的，为了帮助 golangci-lint 用户，这些常见的排除被用作默认排除。

如果你不想使用它可以将 `issues.exclude-use-default` 设置为 `false`。

### EXC0001

+ linter: `errcheck`
+ pattern: `Error return value of .((os\.)?std(out|err)\..*|.*Close|.*Flush|os\.Remove(All)?|.*print(f|ln)?|os\.(Un)?Setenv). is not checked`
+ 为什么：几乎所有程序都会忽略这些函数的错误，在大多数情况下这些函数都能正常运行。

### EXC0002

+ linter: `golint`
+ pattern: `(comment on exported (method|function|type|const)|should have( a package)? comment|comment should be of the form)`
+ why: Annoying issue about not having a comment. The rare codebase has such comments

### EXC0003

+ linter: `golint`
+ pattern: `func name will be used as test\.Test.* by other packages, and that stutters; consider calling this`
+ why: 当测试代码定义在 'test' 包时会误报

### EXC0004

+ linter: `govet`
+ pattern: `(possible misuse of unsafe.Pointer|should have signature)`
+ 为什么：常见的误报

### EXC0005

+ linter: `staticcheck`
+ pattern: `ineffective break statement. Did you mean to break out of the outer loop`
+ 为什么：开发人员倾向于使用 C 风格编写代码，在 `switch` 中带有显式 `break`，因此可以忽略

### EXC0006

+ linter: `gosec`
+ pattern: `Use of unsafe calls should be audited`
+ 为什么：“不安全用法”的误报太多

### EXC0007

+ linter: `gosec`
+ pattern: `Subprocess launch(ed with variable|ing should be audited)`
+ 为什么：使用参数化的 shell 调用时出现了太多的误报

### EXC0008

+ linter: `gosec`
+ pattern: `(G104|G307)`
+ 为什么：跟 errcheck 的检查重复了

### EXC0009

+ linter: `gosec`
+ pattern: `(Expect directory permissions to be 0750 or less|Expect file permissions to be 0600 or less)`
+ 为什么：在一些流行的仓库里出现了太多问题

### EXC0010

+ linter: `gosec`
+ pattern: `Potential file inclusion via variable`
+ 为什么：当出现 `src, err := ioutil.ReadFile(filename)` 时会误报

### EXC0011

+ linter: `stylecheck`
+ pattern: `(comment on exported (method|function|type|const)|should have( a package)? comment|comment should be of the form)`
+ why: Annoying issue about not having a comment. The rare codebase has such comments

### EXC0012

+ linter: `revive`
+ pattern: `exported (.+) should have comment( \(or a comment on this block\))? or be unexported`
+ why: Annoying issue about not having a comment. The rare codebase has such comments

### EXC0013

+ linter: `revive`
+ pattern: `package comment should be of the form "(.+)...`
+ why: Annoying issue about not having a comment. The rare codebase has such comments

### EXC0014

+ linter: `revive`
+ pattern: `comment on exported (.+) should be of the form "(.+)..."`
+ why: Annoying issue about not having a comment. The rare codebase has such comments

### EXC0015

+ linter: `revive`
+ pattern: `should have a package comment`
+ why: Annoying issue about not having a comment. The rare codebase has such comments

