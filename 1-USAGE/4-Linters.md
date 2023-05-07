# Linters

查看支持的 linters 以及哪些 linters 已启用/禁用：

```sh
golangci-lint help linters
```

## 默认启用

| Name | Description | Presets | AutoFix | Since |
| :--: | :---: | :---: | :---: | :---: |
| [errcheck](https://github.com/kisielk/errcheck) [⚙️](#errcheck) | errcheck 是一个用于检查 Go 代码中未检查错误的程序。在某些情况下，这些未经检查的错误可能是严重错误 | bugs, error |  | v1.0.0 |
| [gosimple](https://github.com/dominikh/go-tools/tree/master/simple)[⚙️](#gosimple) | 专门用于精简 Go 源码的 Linter | style |  | v1.20.0 |
| [govet](https://pkg.go.dev/cmd/vet) [⚙️](#govet) | Vet 检查 Go 源代码并报告可疑结构，例如参数与格式字符串不一致的 Printf 调用	| bugs, metalinter |  | v1.0.0 |
| [ineffassign](https://github.com/gordonklaus/ineffassign)	| 检测已存在的变量是否被赋值，但是没有在后续的程序中使用 | unused |  | v1.0.0|
| [staticcheck](https://staticcheck.io/) [⚙️](#staticcheck) | 这是 staticcheck 的一组规则。它与 staticcheck 二进制文件不同。staticcheck 的作者不支持或批准在 golangci-lint 中使用 staticcheck 作为库。 | bugs, metalinter	|  | v1.0.0 |
| typecheck	| 就像 Go 编译器的前端一样，解析和类型检查 Go 代码 | bugs |  | v1.3.0 |
| [unused](https://github.com/dominikh/go-tools/tree/master/unused) | 检查 Go 代码中未使用的常量、变量、函数和类型 | unused |  | v1.20.0 |

## 默认不启用

| Name | Description | Presets | AutoFix | Since |
| :--: | :---: | :---: | :---: | :---: |
| [asasalint](https://github.com/alingse/asasalint) [⚙️](#asasalint) | 检查一个可变参数函数 func(...any) 中，能否使用 []any 作为参数类型 | bugs |  | 1.47.0 |
| [asciicheck](https://github.com/tdakkota/asciicheck) | 用于检查您的代码是否包含非 ASCII 标识符的简单 linter | bugs, style |  | v1.26.0	 |
| [bidichk](https://github.com/breml/bidichk) [⚙️](#bidichk) | 检查是否存在危险的Unicode字符序列 | bugs	|  | 1.43.0	|
| [bodyclose](https://github.com/timakin/bodyclose) | 检查 HTTP 响应体是否关闭成功 | performance, bugs |  | v1.18.0 |
| [containedctx](https://github.com/sivchari/containedctx) | containedctx 是一个检测结构体是否包含 context.Context 字段的 linter | style |  | 1.44.0	 |
| [contextcheck](https://github.com/kkHAIKE/contextcheck) | 检查一个函数是否使用了非继承的上下文 | bugs |  | v1.43.0 |
| [cyclop](https://github.com/bkielbasa/cyclop) [⚙️](#cyclop) | 检查函数和包的圈复杂度 | complexity |  | v1.37.0	|
| [deadcode](https://github.com/remyoudompheng/go-misc/tree/master/deadcode)⚠ | 所有者似乎已经放弃了该 linter。替换为未使用的。 | unused	 |  | v1.0.0 |
| [decorder](https://gitlab.com/bosi/decorder) [⚙️](#decorder) | 检查类型、常量、变量和函数的声明顺序和计数 | format, style 	|  | v1.44.0 |
| [depguard](https://github.com/OpenPeeDeeP/depguard) [⚙️](#depguard) | 检查代码中导入的包名是否在一个可接受的包名列表中 | style, import, module	 |  | v1.4.0 |
| [dogsled](https://github.com/alexkohler/dogsled) [⚙️](#dogsled)	| 检查分配了过多的空白标识符（例如：x, , , _, := f()） | style |  | v1.19.0	 |
| [dupl](https://github.com/mibk/dupl) [⚙️](#dupl) | 代码克隆检测工具 | style	|  | v1.0.0 |
| [dupword](https://github.com/Abirdcfly/dupword) [⚙️](#dupword) | 检查源代码中的重复单词 | comment	| ✔ | 1.50.0 |
| [durationcheck](https://github.com/charithe/durationcheck) | 检查两个时间段相乘的结果 | bugs |  | v1.37.0 |
| [errchkjson](https://github.com/breml/errchkjson) [⚙️](#errchkjson)	| 检查传递给 JSON 编码函数的数据类型，如果发现不支持的数据类型，将会报告错误。此外，它也可以选择性地报告某些情况下，可以省略检查返回的错误的情况。 | bugs	 |  | 1.44.0 |
| [errname](https://github.com/Antonboom/errname) | 检查 sentinel errors 是否以 `Err` 为前缀，并且检查错误类型（error types）是否以 `Error` 为后缀。 | style |  | v1.42.0	|
| [errorlint](https://github.com/polyfloyd/go-errorlint) [⚙️](#errorlint) | errorlint 是一个 linter，用于查找在 Go 1.13 中引入的错误处理机制（即 Error Wrapping Scheme）中可能引起问题的代码。 | bugs, error |  | v1.32.0	 |
| [execinquery](https://github.com/lufeee/execinquery) | execinquery 是一个 linter，用于查询 Query 函数中的查询字符串检查（query string checker）功能，并对读取到的源代码文件进行分析，发现其中的问题并给出相应的警告。 | sql	|  | v1.46.0 |
| [exhaustive](https://github.com/nishanths/exhaustive) [⚙️](#exhaustive) | 当使用枚举类型进行 switch 语句判断时，检查代码的全面性 | bugs |  | v1.28.0	 |
| [exhaustivestruct](https://github.com/mbilski/exhaustivestruct) [⚙️](#exhaustivestruct) ⚠	| 所有者似乎已经放弃了该 linter。取而代之的是 exhaustruct | style, test |  | v1.32.0 |
| [exhaustruct](https://github.com/GaijinEntertainment/go-exhaustruct) [⚙️](#exhaustruct) | 检查结构体的所有字段是否都已经被初始化 | style, test |  | v1.46.0	|
| [exportloopref](https://github.com/kyoh86/exportloopref) | 检查是否存在指向循环体内定义的变量的指针 | bugs |  | v1.28.0	|
| [forbidigo](https://github.com/ashanbrown/forbidigo) [⚙️](#forbidigo) | 禁止标识符 | style |  | v1.34.0 |
| [forcetypeassert](https://github.com/gostaticanalysis/forcetypeassert) | 寻找强制类型断言 | style |  | v1.38.0 |
| [funlen](https://github.com/ultraware/funlen) [⚙️](#funlen) | 长函数检测工具 | complexity |  | v1.18.0 |
| [gci](https://github.com/daixiang0/gci) [⚙️](#gci) | GCI 控制 Go 包的导入顺序，并始终使其具有确定性。 | format, import |  | v1.30.0	|
| [ginkgolinter](https://github.com/nunnatsa/ginkgolinter) [⚙️](#ginkgolinter) | 强制使用 Ginkgo 和 Gomega 标准 |  style |  | v1.51.0 |
| [gocheckcompilerdirectives](https://github.com/leighmcculloch/gocheckcompilerdirectives) | 检查 go 编译器指令注释 (//go:) 是否有效。 | bugs |  | v1.51.0 |
| [gochecknoglobals](https://github.com/leighmcculloch/gochecknoglobals) | 检查是否存在全局变量<br />该分析器会检查是否存在全局变量，并在发现任何全局变量时报错。<br />全局变量是在包范围内声明的变量，可以被包中的任何函数读取和写入。全局变量可能会导致副作用，难以跟踪。一个函数中的代码可能会改变变量的状态，而与之无关的另一部分代码可能会受到影响。 | style |  | v1.12.0 |
| gochecknoinits | 检查代码中是否包含 init 函数 | style |  | v1.12.0 |
| [gocognit](https://github.com/uudashr/gocognit) [⚙️](#gocognit)	| 计算和检查函数的认知复杂度 | complexity |  | v1.20.0 |
| [goconst](https://github.com/jgautheron/goconst) [⚙️](#goconst) | 查找可以用常量替换的重复字符串 | style |  | v1.0.0 |
| [gocritic](https://github.com/go-critic/go-critic) [⚙️](#gocritic) | 提供了一个诊断工具，它可以通过动态规则检查代码中的错误、性能和风格问题。<br/>它不需要重新编译就能添加新的规则来实现扩展。<br/>这些动态规则是用AST模式、过滤器、报告消息和可选建议来声明的。 | style, metalinter	 |  | v1.12.0	|
| [gocyclo](https://github.com/fzipp/gocyclo) [⚙️](#gocyclo) | 计算和检查函数的圈复杂度 | complexity |  | v1.0.0 |
| [godot](https://github.com/tetafro/godot) [⚙️](#godot) | 检查注释是否以句号结尾 | style, comment | ✔ | v1.25.0 |
| [godox](https://github.com/matoous/godox) [⚙️](#godox) | 可以检测代码注释中的特定关键词如 FIXME，TODO 的工具 | style, comment	|  | v1.19.0 |
| [goerr113](https://github.com/Djarvur/go-err113) | 检查代码中处理错误的表达式是否存在问题 | style, error |  | v1.26.0	|
| [gofmt](https://pkg.go.dev/cmd/gofmt) [⚙️](#gofmt) | Gofmt 检查代码是否格式化过。默认情况下该工具使用 -s 选项来运行检查代码简化 | format | ✔ | v1.0.0	|
| [gofumpt](https://github.com/mvdan/gofumpt) [⚙️](#gofumpt) | Gofumpt 检查代码是否被 gofumpt 格式化过。 | format | ✔ | v1.28.0 |
| [goheader](https://github.com/denis-tingaikin/go-header) [⚙️](#goheader) | 检查文件头是否与模式匹配 | style |  | v1.28.0	 |
| [goimports](https://pkg.go.dev/golang.org/x/tools/cmd/goimports) [⚙️](#goimports) | 检查代码中的import语句是否符合Go语言官方命令"goimports"的格式规范，如果不符合则使用自动修复模式对其进行重新格式化。 | format, import	 | ✔ | v1.20.0 |
| [golint](https://github.com/golang/lint) [⚙️](#golint) ⚠ | 该 linter 仓库已被所有者归档，不再维护。由 revive 代替。 | style |  | v1.0.0 |
| [gomnd](https://github.com/tommy-muehle/go-mnd) [⚙️](#gomnd) | 一个分析工具，可以检测出 magic number。 | style |  | v1.22.0 |
| [gomoddirectives](https://github.com/ldez/gomoddirectives) [⚙️](#gomoddirectives) |	管理 go.mod 中“replace”、“retract”和“excludes”指令的使用。 | style, module	|  | v1.39.0 |
| [gomodguard](https://github.com/ryancurrah/gomodguard) [⚙️](#gomodguard) | direct Go module dependencies 用于检查Go项目中的依赖项列表。该工具有一个允许/阻止列表，可以根据这些列表中的条目来确定哪些依赖项是被允许/禁止的。它与 depguard 不同，后者具有不同的阻止类型，例如版本约束和模块建议。 | style, import, module	 | | v1.25.0 |
| [goprintffuncname](https://github.com/jirfag/go-printf-func-name) | 检查类似于 printf 函数的函数是否以字符 `f` 结尾命名 | style |  | v1.23.0	 |
| [gosec](https://github.com/securego/gosec) [⚙️](#gosec) | 检查源代码是否存在安全问题 | bugs |  | v1.0.0	|
| [gosmopolitan](https://github.com/xen0n/gosmopolitan) [⚙️](#gosmopolitan) | 在 Go 代码库中报告一些错误的国际化/本地化（i18n/l10n）的模式 | bugs |  | v1.53.0 |
| [grouper](https://github.com/leonklingele/grouper) [⚙️](#grouper) | 一个分析表达式组的分析器 | style |  | v1.44.0 |
| [ifshort](https://github.com/esimonov/ifshort) [⚙️](#ifshort) ⚠ | 作者已弃用该 linter 仓库 | style |  | v1.36.0 |
| [importas](https://github.com/julz/importas) [⚙️](#importas) | 强制规定统一的导入别名 | style |  | v1.38.0 |
| [interfacebloat](https://github.com/sashamelentyev/interfacebloat) [⚙️](#interfacebloat) | 检查接口里的方法数量 | style | | v1.49.0	 |
| [interfacer](https://github.com/mvdan/interfacer) ⚠	| 作者已弃用该 linter 仓库 | style |  | v1.36.0 |
| [ireturn](https://github.com/butuzov/ireturn) [⚙️](#ireturn) | 接收接口，返回具体类型 | style |  | v1.43.0 |
| lll [⚙️](#lll) | Reports long lines	| style |  | v1.8.0	|
| [loggercheck](https://github.com/timonwong/loggercheck) [⚙️](#loggercheck) | 检查常见日志记录器库（如kitlog、klog、logr、zap）中的键值对。 | style, bugs	 |  | v1.49.0 |
| [maintidx](https://github.com/yagipy/maintidx) [⚙️](#maintidx) | maintidx 用于计算每个函数的可维护性指数 | complexity |  | v1.44.0	|
| [makezero](https://github.com/ashanbrown/makezero) [⚙️](#makezero) | 寻找声明 slice 时初始长度不为零的情况 | style, bugs	|  | v1.34.0 |
| [maligned](https://github.com/mdempsky/maligned) [⚙️](#maligned) ⚠ | 该仓库已被作者归档，由 govet 'fieldalignment' 替代。 | performance |  | v1.0.0 |
| [misspell](https://github.com/client9/misspell) [⚙️](#misspell) | 查找注释中经常拼写错误的英语单词 | style, comment	| ✔ | v1.8.0 |
| [musttag](https://github.com/tmzane/musttag) [⚙️](#musttag) | 序列化（反序列化）结构体时强制执行 field tags | style, bugs |  | v1.51.0 |
| [nakedret](https://github.com/alexkohler/nakedret) [⚙️](#nakedret) | 寻找函数长度超过特定的值并且在函数中存在“裸”返回的情况 | bugs |  | v1.38.0	|
| [nestif](https://github.com/nakabonne/nestif) [⚙️](#nestif)	| 报告深度嵌套的 if 语句 | complexity	|  | v1.25.0 |
| [nilerr](https://github.com/gostaticanalysis/nilerr) | 查找返回 nil 的代码，即使它检查到 error 不为 nil。 | bugs |  | v1.38.0 |
| [nilnil](https://github.com/Antonboom/nilnil) [⚙️](#nilnil) | 检查是否存在同时返回 `nil` 错误和无效值。 | style	|  | v1.43.0 |
| [nlreturn](https://github.com/ssgreg/nlreturn) [⚙️](#nlreturn) | nlreturn 在 return 和分支语句之前检查新行以提高代码清晰度 | style |  | v1.30.0 |
| [noctx](https://github.com/sonatard/noctx) | noctx 查找发送 http 请求没有携带 context.Context 的场景 | performance, bugs	 | | v1.28.0 |
| [nolintlint](https://github.com/golangci/golangci-lint/blob/master/pkg/golinters/nolintlint/README.md) [⚙️](#nolintlint) | 报告格式不正确或不完整的 nolint 指令 | style |  | v1.26.0 |
| [nonamedreturns](https://github.com/firefart/nonamedreturns) [⚙️](#nonamedreturns) | 报告所有命名返回 | style	|  | v1.46.0 |
| [nosnakecase](https://github.com/sivchari/nosnakecase) ⚠	| 该 linter 库已被作者弃用。替换为 revive（var-naming） | style	|  | v1.47.0 |
| [nosprintfhostport](https://github.com/stbenjam/no-sprintf-host-port) | 检查代码中是否误用 Sprintf 方法来构建主机地址：包含端口号的 URL | style |  | v1.46.0	 |
| [paralleltest](https://github.com/kunwardeep/paralleltest) [⚙️](#paralleltest) | paralleltest 可以检测没有使用 t.Parallel() 方法的测试函数（优化你的测试并发性能） | style, test	 |  | v1.33.0 |
| [prealloc](https://github.com/alexkohler/prealloc) [⚙️](#prealloc) | 寻找可能可以预先分配内存空间的切片声明 | performance |  | v1.19.0	 |
| [predeclared](https://github.com/nishanths/predeclared) [⚙️](#predeclared) | 寻找屏蔽了 Go 语言的预定义标识符的代码 | style |  | v1.35.0 |
| [promlinter](https://github.com/yeya24/promlinter) [⚙️](#promlinter) | 通过 promlint 检查 Prometheus 指标命名 | style |  | v1.40.0 |
| [reassign](https://github.com/curioswitch/go-reassign) [⚙️](#reassign) | 检查包变量没有被重新分配 | bugs |  | 1.49.0 |
| [revive](https://github.com/mgechev/revive) [⚙️](#revive) | 快速、可配置、可扩展、灵活且美观的 Go linter。直接替换 golint。 | style, metalinter	 |  | v1.37.0 |
| [rowserrcheck](https://github.com/jingyugao/rowserrcheck) [⚙️](#rowserrcheck) | 检查 rows 的 Err 是否被成功地检查 | bugs, sql |  | v1.23.0 |
| [scopelint](https://github.com/kyoh86/scopelint) ⚠ | 该 linter 库已被作者弃用。替换为 exportloopref。 | bugs |  | v1.12.0	|
| [sqlclosecheck](https://github.com/ryanrolds/sqlclosecheck) | 检查 sql.Rows 和 sql.Stmt 是否关闭 | bugs, sql | | v1.28.0	 |
| [structcheck](https://github.com/opennota/check) [⚙️](#structcheck) ⚠	| 该 linter 库已被作者弃用。替换为 unused | unused |  | v1.0.0 |
| [stylecheck](https://github.com/dominikh/go-tools/tree/master/stylecheck) [⚙️](#stylecheck) | stylecheck 是 golint 的一个替代 | style |  | v1.20.0	 |
| [tagalign](https://github.com/4meepo/tagalign) [⚙️](#tagalign) | 检查结构体标签是否对齐 | style, format	| ✔	| v1.53.0 |
| [tagliatelle](https://github.com/ldez/tagliatelle) [⚙️](#tagliatelle) | 检查结构体标签 | style |  | v1.40.0 |
| [tenv](https://github.com/sivchari/tenv) [⚙️](#tenv) | tenv 是一个分析器，在大于 Go1.17 版本中检测使用 os.Setenv 而不是 t.Setenv | style	 |  | v1.43.0	|
| [testableexamples](https://github.com/maratori/testableexamples) | linter 检查示例是否可测试（具有预期的输出） | test |  | v1.50.0 |
| [testpackage](https://github.com/maratori/testpackage) [⚙️](#testpackage) | 能让你使用的一个独立测试包 | style, test |  | v1.25.0	|
| [thelper](https://github.com/kulti/thelper) [⚙️](#thelper) | 用于检测 Go 测试中是否存在未经 t.Helper() 调用的测试辅助函数，并且检查测试辅助函数的一致性。 | style |  | v1.43.0	|
| [tparallel](https://github.com/moricho/tparallel) | tparallel 用于检测你的 Go 测试代码中是否存在不合理使用 t.Parallel() 的情况 | style, test	 |  | v1.32.0	|
| [unconvert](https://github.com/mdempsky/unconvert) | 删除不必要的类型转换 | style |  | v1.0.0	|
| [unparam](https://github.com/mvdan/unparam) [⚙️](#unparam) | 报告未使用的函数参数 | unused |  | v1.9.0 |
| [usestdlibvars](https://github.com/sashamelentyev/usestdlibvars) [⚙️](#usestdlibvars)	| 检测可能可以使用 go 标准库变量或常量的场景 | style |  | v1.48.0	|
| [varcheck](https://github.com/opennota/check) [⚙️](#varcheck) ⚠ | 该 linter 库已被作者弃用。替换为 unused。 | unused | | v1.0.0	|
| [varnamelen](https://github.com/blizzy78/varnamelen) [⚙️](#varnamelen) | 检查变量名的长度是否与其作用域匹配 | style	|  | v1.43.0 |
| [wastedassign](https://github.com/sanposhiho/wastedassign) | wastedassign 查找无用的赋值语句 | style |  | v1.38.0 |
| [whitespace](https://github.com/ultraware/whitespace) [⚙️](#whitespace) | 检测前后是否有空格的工具 | style | ✔ | v1.19.0	 |
| [wrapcheck](https://github.com/tomarrell/wrapcheck) [⚙️](#wrapcheck) | 检查外部包返回的错误是否被包裹 | style, error	 |  | v1.32.0	|
| [wsl](https://github.com/bombsimon/wsl) [⚙️](#wsl) | Whitespace Linter - 强制你使用空行 | style	|  | v1.20.0 |
| [zerologlint](https://github.com/ykadowak/zerologlint) | 检测用户使用 `zerolog` 时忘记调用 `Send` 或者 `Msg` 方法来发送日志消息。 | bugs |  | v1.53.0 |

### asasalint

```yaml
linters-settings:
  asasalint:
    # To specify a set of function names to exclude.
    # The values are merged with the builtin exclusions.
    # The builtin exclusions can be disabled by setting `use-builtin-exclusions` to `false`.
    # Default: ["^(fmt|log|logger|t|)\.(Print|Fprint|Sprint|Fatal|Panic|Error|Warn|Warning|Info|Debug|Log)(|f|ln)$"]
    exclude:
      - Append
      - \.Wrapf
    # To enable/disable the asasalint builtin exclusions of function names.
    # See the default value of `exclude` to get the builtin exclusions.
    # Default: true
    use-builtin-exclusions: false
    # Ignore *_test.go files.
    # Default: false
    ignore-test: true
```

### bidichk

```yaml
linters-settings:
  bidichk:
    # The following configurations check for all mentioned invisible unicode runes.
    # All runes are enabled by default.
    left-to-right-embedding: false
    right-to-left-embedding: false
    pop-directional-formatting: false
    left-to-right-override: false
    right-to-left-override: false
    left-to-right-isolate: false
    right-to-left-isolate: false
    first-strong-isolate: false
    pop-directional-isolate: false
```

### cyclop

```yaml
linters-settings:
  cyclop:
    # The maximal code complexity to report.
    # Default: 10
    max-complexity: 10
    # The maximal average package complexity.
    # If it's higher than 0.0 (float) the check is enabled
    # Default: 0.0
    package-average: 0.5
    # Should ignore tests.
    # Default: false
    skip-tests: true
```

### decorder

```yaml
linters-settings:
  decorder:
    # Required order of `type`, `const`, `var` and `func` declarations inside a file.
    # Default: types before constants before variables before functions.
    dec-order:
      - type
      - const
      - var
      - func
    # If true, order of declarations is not checked at all.
    # Default: true (disabled)
    disable-dec-order-check: false
    # If true, `init` func can be anywhere in file (does not have to be declared before all other functions).
    # Default: true (disabled)
    disable-init-func-first-check: false
    # If true, multiple global `type`, `const` and `var` declarations are allowed.
    # Default: true (disabled)
    disable-dec-num-check: false
```

### depguard

```yaml
linters-settings:
  depguard:
    # Rules to apply.
    #
    # Variables:
    # - File Variables
    #   you can still use and exclamation mark ! in front of a variable to say not to use it.
    #   Example !$test will match any file that is not a go test file.
    #
    #   `$all` - matches all go files
    #   `$test` - matches all go test files
    #
    # - Package Variables
    #
    #  `$gostd` - matches all of go's standard library (Pulled from `GOROOT`)
    #
    # Default: no rules.
    rules:
      # Name of a rule.
      main:
        # List of file globs that will match this list of settings to compare against.
        # Default: $all
        files:
          - "!**/*_a _file.go"
        # List of allowed packages.
        allow:
          - $gostd
          - github.com/OpenPeeDeeP
        # Packages that are not allowed where the value is a suggestion.
        deny:
          - pkg: "github.com/sirupsen/logrus"
            desc: not allowed
          - pkg: "github.com/pkg/errors"
            desc: Should be replaced by standard lib errors package
```

### dogsled

```yaml
linters-settings:
  dogsled:
    # Checks assignments with too many blank identifiers.
    # Default: 2
    max-blank-identifiers: 3
```

### dupl

```yaml
linters-settings:
  dupl:
    # Tokens count to trigger issue.
    # Default: 150
    threshold: 100
```

### dupword

```yaml
linters-settings:
  dupword:
    # Keywords for detecting duplicate words.
    # If this list is not empty, only the words defined in this list will be detected.
    # Default: []
    keywords:
      - "the"
      - "and"
      - "a"
```

### errcheck

```yaml
linters-settings:
  errcheck:
    # Report about not checking of errors in type assertions: `a := b.(MyStruct)`.
    # Such cases aren't reported by default.
    # Default: false
    check-type-assertions: true
    # report about assignment of errors to blank identifier: `num, _ := strconv.Atoi(numStr)`.
    # Such cases aren't reported by default.
    # Default: false
    check-blank: true
    # DEPRECATED comma-separated list of pairs of the form pkg:regex
    #
    # the regex is used to ignore names within pkg. (default "fmt:.*").
    # see https://github.com/kisielk/errcheck#the-deprecated-method for details
    ignore: fmt:.*,io/ioutil:^Read.*
    # To disable the errcheck built-in exclude list.
    # See `-excludeonly` option in https://github.com/kisielk/errcheck#excluding-functions for details.
    # Default: false
    disable-default-exclusions: true
    # DEPRECATED use exclude-functions instead.
    #
    # Path to a file containing a list of functions to exclude from checking.
    # See https://github.com/kisielk/errcheck#excluding-functions for details.
    exclude: /path/to/file.txt
    # List of functions to exclude from checking, where each entry is a single function to exclude.
    # See https://github.com/kisielk/errcheck#excluding-functions for details.
    exclude-functions:
      - io/ioutil.ReadFile
      - io.Copy(*bytes.Buffer)
      - io.Copy(os.Stdout)
```

### errchkjson

```yaml
linters-settings:
  errchkjson:
    # With check-error-free-encoding set to true, errchkjson does warn about errors
    # from json encoding functions that are safe to be ignored,
    # because they are not possible to happen.
    #
    # if check-error-free-encoding is set to true and errcheck linter is enabled,
    # it is recommended to add the following exceptions to prevent from false positives:
    #
    #     linters-settings:
    #       errcheck:
    #         exclude-functions:
    #           - encoding/json.Marshal
    #           - encoding/json.MarshalIndent
    #
    # Default: false
    check-error-free-encoding: true
    # Issue on struct encoding that doesn't have exported fields.
    # Default: false
    report-no-exported: false
```

### errorlint

```yaml
linters-settings:
  errorlint:
    # Check whether fmt.Errorf uses the %w verb for formatting errors.
    # See the https://github.com/polyfloyd/go-errorlint for caveats.
    # Default: true
    errorf: false
    # Permit more than 1 %w verb, valid per Go 1.20 (Requires errorf:true)
    # Default: true
    errorf-multi: false
    # Check for plain type assertions and type switches.
    # Default: true
    asserts: false
    # Check for plain error comparisons.
    # Default: true
    comparison: false
```

### exhaustive

```yaml
linters-settings:
  exhaustive:
    # Program elements to check for exhaustiveness.
    # Default: [ switch ]
    check:
      - switch
      - map
    # Check switch statements in generated files also.
    # Default: false
    check-generated: true
    # Presence of "default" case in switch statements satisfies exhaustiveness,
    # even if all enum members are not listed.
    # Default: false
    default-signifies-exhaustive: true
    # Enum members matching the supplied regex do not have to be listed in
    # switch statements to satisfy exhaustiveness.
    # Default: ""
    ignore-enum-members: "Example.+"
    # Enum types matching the supplied regex do not have to be listed in
    # switch statements to satisfy exhaustiveness.
    # Default: ""
    ignore-enum-types: "Example.+"
    # Consider enums only in package scopes, not in inner scopes.
    # Default: false
    package-scope-only: true
    # Only run exhaustive check on switches with "//exhaustive:enforce" comment.
    # Default: false
    explicit-exhaustive-switch: true
    # Only run exhaustive check on map literals with "//exhaustive:enforce" comment.
    # Default: false
    explicit-exhaustive-map: true
```

### exhaustivestruct

```yaml
linters-settings:
  exhaustivestruct:
    # Struct Patterns is list of expressions to match struct packages and names.
    # The struct packages have the form `example.com/package.ExampleStruct`.
    # The matching patterns can use matching syntax from https://pkg.go.dev/path#Match.
    # If this list is empty, all structs are tested.
    # Default: []
    struct-patterns:
      - '*.Test'
      - 'example.com/package.ExampleStruct'
```

### exhaustruct

```yaml
linters-settings:
  exhaustruct:
    # List of regular expressions to match struct packages and names.
    # If this list is empty, all structs are tested.
    # Default: []
    include:
      - '.*\.Test'
      - 'example\.com/package\.ExampleStruct[\d]{1,2}'
    # List of regular expressions to exclude struct packages and names from check.
    # Default: []
    exclude:
      - 'cobra\.Command$'
```

### forbidigo

```yaml
linters-settings:
  forbidigo:
    # Forbid the following identifiers (list of regexp).
    # Default: ["^(fmt\\.Print(|f|ln)|print|println)$"]
    forbid:
      - ^print.*$
      - 'fmt\.Print.*'
      # Optionally put comments at the end of the regex, surrounded by `(# )?`
      # Escape any special characters.
      - 'fmt\.Print.*(# Do not commit print statements\.)?'
    # Exclude godoc examples from forbidigo checks.
    # Default: true
    exclude_godoc_examples: false
```

### funlen

```yaml
linters-settings:
  funlen:
    # Checks the number of lines in a function.
    # If lower than 0, disable the check.
    # Default: 60
    lines: -1
    # Checks the number of statements in a function.
    # If lower than 0, disable the check.
    # Default: 40
    statements: -1
```

### gci

```yaml
linters-settings:
  gci:
    # DEPRECATED: use `sections` and `prefix(github.com/org/project)` instead.
    local-prefixes: github.com/org/project
    # Section configuration to compare against.
    # Section names are case-insensitive and may contain parameters in ().
    # The default order of sections is `standard > default > custom > blank > dot`,
    # If `custom-order` is `true`, it follows the order of `sections` option.
    # Default: ["standard", "default"]
    sections:
      - standard # Standard section: captures all standard packages.
      - default # Default section: contains all imports that could not be matched to another section type.
      - prefix(github.com/org/project) # Custom section: groups all imports with the specified Prefix.
      - blank # Blank section: contains all blank imports. This section is not present unless explicitly enabled.
      - dot # Dot section: contains all dot imports. This section is not present unless explicitly enabled.
    # Skip generated files.
    # Default: true
    skip-generated: false
    # Enable custom order of sections.
    # If `true`, make the section order the same as the order of `sections`.
    # Default: false
    custom-order: true
```

### ginkgolinter

```yaml
linters-settings:
  ginkgolinter:
    # Suppress the wrong length assertion warning.
    # Default: false
    suppress-len-assertion: true
    # Suppress the wrong nil assertion warning.
    # Default: false
    suppress-nil-assertion: true
    # Suppress the wrong error assertion warning.
    # Default: false
    suppress-err-assertion: true
    # Suppress the wrong comparison assertion warning.
    # Default: false
    suppress-compare-assertion: true
    # Suppress the function all in async assertion warning.
    # Default: false
    suppress-async-assertion: true
    # Don't trigger warnings for HaveLen(0)
    # Default: false
    allow-havelen-zero: true
```

### gocognit

```yaml
linters-settings:
  gocognit:
    # Minimal code complexity to report.
    # Default: 30 (but we recommend 10-20)
    min-complexity: 10
```

### goconst

```yaml
linters-settings:
  goconst:
    # Minimal length of string constant.
    # Default: 3
    min-len: 2
    # Minimum occurrences of constant string count to trigger issue.
    # Default: 3
    min-occurrences: 2
    # Ignore test files.
    # Default: false
    ignore-tests: true
    # Look for existing constants matching the values.
    # Default: true
    match-constant: false
    # Search also for duplicated numbers.
    # Default: false
    numbers: true
    # Minimum value, only works with goconst.numbers
    # Default: 3
    min: 2
    # Maximum value, only works with goconst.numbers
    # Default: 3
    max: 2
    # Ignore when constant is not used as function argument.
    # Default: true
    ignore-calls: false
```

### gocritic

```yaml
linters-settings:
  gocritic:
    # Which checks should be enabled; can't be combined with 'disabled-checks'.
    # See https://go-critic.github.io/overview#checks-overview.
    # To check which checks are enabled run `GL_DEBUG=gocritic golangci-lint run`.
    # By default, list of stable checks is used.
    enabled-checks:
      - nestingReduce
      - unnamedResult
      - ruleguard
      - truncateCmp
    # Which checks should be disabled; can't be combined with 'enabled-checks'.
    # Default: []
    disabled-checks:
      - regexpMust
    # Enable multiple checks by tags, run `GL_DEBUG=gocritic golangci-lint run` to see all tags and checks.
    # See https://github.com/go-critic/go-critic#usage -> section "Tags".
    # Default: []
    enabled-tags:
      - diagnostic
      - style
      - performance
      - experimental
      - opinionated
    disabled-tags:
      - diagnostic
      - style
      - performance
      - experimental
      - opinionated
    # Settings passed to gocritic.
    # The settings key is the name of a supported gocritic checker.
    # The list of supported checkers can be find in https://go-critic.github.io/overview.
    settings:
      # Must be valid enabled check name.
      captLocal:
        # Whether to restrict checker to params only.
        # Default: true
        paramsOnly: false
      elseif:
        # Whether to skip balanced if-else pairs.
        # Default: true
        skipBalanced: false
      hugeParam:
        # Size in bytes that makes the warning trigger.
        # Default: 80
        sizeThreshold: 70
      nestingReduce:
        # Min number of statements inside a branch to trigger a warning.
        # Default: 5
        bodyWidth: 4
      rangeExprCopy:
        # Size in bytes that makes the warning trigger.
        # Default: 512
        sizeThreshold: 516
        # Whether to check test functions
        # Default: true
        skipTestFuncs: false
      rangeValCopy:
        # Size in bytes that makes the warning trigger.
        # Default: 128
        sizeThreshold: 32
        # Whether to check test functions.
        # Default: true
        skipTestFuncs: false
      ruleguard:
        # Enable debug to identify which 'Where' condition was rejected.
        # The value of the parameter is the name of a function in a ruleguard file.
        #
        # When a rule is evaluated:
        # If:
        #   The Match() clause is accepted; and
        #   One of the conditions in the Where() clause is rejected,
        # Then:
        #   ruleguard prints the specific Where() condition that was rejected.
        #
        # The flag is passed to the ruleguard 'debug-group' argument.
        # Default: ""
        debug: 'emptyDecl'
        # Deprecated, use 'failOn' param.
        # If set to true, identical to failOn='all', otherwise failOn=''
        failOnError: false
        # Determines the behavior when an error occurs while parsing ruleguard files.
        # If flag is not set, log error and skip rule files that contain an error.
        # If flag is set, the value must be a comma-separated list of error conditions.
        # - 'all':    fail on all errors.
        # - 'import': ruleguard rule imports a package that cannot be found.
        # - 'dsl':    gorule file does not comply with the ruleguard DSL.
        # Default: ""
        failOn: dsl
        # Comma-separated list of file paths containing ruleguard rules.
        # If a path is relative, it is relative to the directory where the golangci-lint command is executed.
        # The special '${configDir}' variable is substituted with the absolute directory containing the golangci config file.
        # Glob patterns such as 'rules-*.go' may be specified.
        # Default: ""
        rules: '${configDir}/ruleguard/rules-*.go,${configDir}/myrule1.go'
        # Comma-separated list of enabled groups or skip empty to enable everything.
        # Tags can be defined with # character prefix.
        # Default: "<all>"
        enable: "myGroupName,#myTagName"
        # Comma-separated list of disabled groups or skip empty to enable everything.
        # Tags can be defined with # character prefix.
        # Default: ""
        disable: "myGroupName,#myTagName"
      tooManyResultsChecker:
        # Maximum number of results.
        # Default: 5
        maxResults: 10
      truncateCmp:
        # Whether to skip int/uint/uintptr types.
        # Default: true
        skipArchDependent: false
      underef:
        # Whether to skip (*x).method() calls where x is a pointer receiver.
        # Default: true
        skipRecvDeref: false
      unnamedResult:
        # Whether to check exported functions.
        # Default: false
        checkExported: true
```

### gocyclo

```yaml
linters-settings:
  gocyclo:
    # Minimal code complexity to report.
    # Default: 30 (but we recommend 10-20)
    min-complexity: 10
```

### godot

```yaml
linters-settings:
  godot:
    # Comments to be checked: `declarations`, `toplevel`, or `all`.
    # Default: declarations
    scope: toplevel
    # List of regexps for excluding particular comment lines from check.
    # Default: []
    exclude:
      # Exclude todo and fixme comments.
      - "^fixme:"
      - "^todo:"
    # Check that each sentence ends with a period.
    # Default: true
    period: false
    # Check that each sentence starts with a capital letter.
    # Default: false
    capital: true
```

### godox

```yaml
linters-settings:
  godox:
    # Report any comments starting with keywords, this is useful for TODO or FIXME comments that
    # might be left in the code accidentally and should be resolved before merging.
    # Default: ["TODO", "BUG", "FIXME"]
    keywords:
      - NOTE
      - OPTIMIZE # marks code that should be optimized before merging
      - HACK # marks hack-around that should be removed before merging
```

### gofmt

```yaml
linters-settings:
  gofmt:
    # Simplify code: gofmt with `-s` option.
    # Default: true
    simplify: false
    # Apply the rewrite rules to the source before reformatting.
    # https://pkg.go.dev/cmd/gofmt
    # Default: []
    rewrite-rules:
      - pattern: 'interface{}'
        replacement: 'any'
      - pattern: 'a[b:len(a)]'
        replacement: 'a[b:]'
```

### gofumpt

```yaml
linters-settings:
  gofumpt:
    # Deprecated: use the global `run.go` instead.
    lang-version: "1.17"
    # Module path which contains the source code being formatted.
    # Default: ""
    module-path: github.com/org/project
    # Choose whether to use the extra rules.
    # Default: false
    extra-rules: true
```

### goheader

```yaml
linters-settings:
  goheader:
    # Supports two types 'const` and `regexp`.
    # Values can be used recursively.
    # Default: {}
    values:
      const:
        # Define here const type values in format k:v.
        # For example:
        COMPANY: MY COMPANY
      regexp:
        # Define here regexp type values.
        # for example:
        AUTHOR: .*@mycompany\.com
    # The template use for checking.
    # Default: ""
    template: |-
      # Put here copyright header template for source code files
      # For example:
      # Note: {{ YEAR }} is a builtin value that returns the year relative to the current machine time.
      #
      # {{ AUTHOR }} {{ COMPANY }} {{ YEAR }}
      # SPDX-License-Identifier: Apache-2.0

      # Licensed under the Apache License, Version 2.0 (the "License");
      # you may not use this file except in compliance with the License.
      # You may obtain a copy of the License at:

      #   http://www.apache.org/licenses/LICENSE-2.0

      # Unless required by applicable law or agreed to in writing, software
      # distributed under the License is distributed on an "AS IS" BASIS,
      # WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
      # See the License for the specific language governing permissions and
      # limitations under the License.
    # As alternative of directive 'template', you may put the path to file with the template source.
    # Useful if you need to load the template from a specific file.
    # Default: ""
    template-path: /path/to/my/template.tmpl
```

### goimports

```yaml
linters-settings:
  goimports:
    # A comma-separated list of prefixes, which, if set, checks import paths
    # with the given prefixes are grouped after 3rd-party packages.
    # Default: ""
    local-prefixes: github.com/org/project
```

### golint

```yaml
linters-settings:
  golint:
    # Minimal confidence for issues.
    # Default: 0.8
    min-confidence: 0.7
```

### gomnd

```yaml
linters-settings:
  gomnd:
    # List of enabled checks, see https://github.com/tommy-muehle/go-mnd/#checks for description.
    # Default: ["argument", "case", "condition", "operation", "return", "assign"]
    checks:
      - argument
      - case
      - condition
      - operation
      - return
      - assign
    # List of numbers to exclude from analysis.
    # The numbers should be written as string.
    # Values always ignored: "1", "1.0", "0" and "0.0"
    # Default: []
    ignored-numbers:
      - '0666'
      - '0755'
      - '42'
    # List of file patterns to exclude from analysis.
    # Values always ignored: `.+_test.go`
    # Default: []
    ignored-files:
      - 'magic1_.+\.go$'
    # List of function patterns to exclude from analysis.
    # Following functions are always ignored: `time.Date`,
    # `strconv.FormatInt`, `strconv.FormatUint`, `strconv.FormatFloat`,
    # `strconv.ParseInt`, `strconv.ParseUint`, `strconv.ParseFloat`.
    # Default: []
    ignored-functions:
      - '^math\.'
      - '^http\.StatusText$'
```

### gomoddirectives

```yaml
linters-settings:
  gomoddirectives:
    # Allow local `replace` directives.
    # Default: false
    replace-local: false
    # List of allowed `replace` directives.
    # Default: []
    replace-allow-list:
      - launchpad.net/gocheck
    # Allow to not explain why the version has been retracted in the `retract` directives.
    # Default: false
    retract-allow-no-explanation: false
    # Forbid the use of the `exclude` directives.
    # Default: false
    exclude-forbidden: false
```

### gomodguard

```yaml
linters-settings:
  gomodguard:
    allowed:
      # List of allowed modules.
      # Default: []
      modules:
        - gopkg.in/yaml.v2
      # List of allowed module domains.
      # Default: []
      domains:
        - golang.org
    blocked:
      # List of blocked modules.
      # Default: []
      modules:
        # Blocked module.
        - github.com/uudashr/go-module:
            # Recommended modules that should be used instead. (Optional)
            recommendations:
              - golang.org/x/mod
            # Reason why the recommended module should be used. (Optional)
            reason: "`mod` is the official go.mod parser library."
      # List of blocked module version constraints.
      # Default: []
      versions:
        # Blocked module with version constraint.
        - github.com/mitchellh/go-homedir:
            # Version constraint, see https://github.com/Masterminds/semver#basic-comparisons.
            version: "< 1.1.0"
            # Reason why the version constraint exists. (Optional)
            reason: "testing if blocked version constraint works."
      # Set to true to raise lint issues for packages that are loaded from a local path via replace directive.
      # Default: false
      local_replace_directives: false
```

### gosimple

```yaml
linters-settings:
  gosimple:
    # Deprecated: use the global `run.go` instead.
    go: "1.15"
    # Sxxxx checks in https://staticcheck.io/docs/configuration/options/#checks
    # Default: ["*"]
    checks: ["all"]
```

### gosec

```yaml
linters-settings:
  gosec:
    # To select a subset of rules to run.
    # Available rules: https://github.com/securego/gosec#available-rules
    # Default: [] - means include all rules
    includes:
      - G101 # Look for hard coded credentials
      - G102 # Bind to all interfaces
      - G103 # Audit the use of unsafe block
      - G104 # Audit errors not checked
      - G106 # Audit the use of ssh.InsecureIgnoreHostKey
      - G107 # Url provided to HTTP request as taint input
      - G108 # Profiling endpoint automatically exposed on /debug/pprof
      - G109 # Potential Integer overflow made by strconv.Atoi result conversion to int16/32
      - G110 # Potential DoS vulnerability via decompression bomb
      - G111 # Potential directory traversal
      - G112 # Potential slowloris attack
      - G113 # Usage of Rat.SetString in math/big with an overflow (CVE-2022-23772)
      - G114 # Use of net/http serve function that has no support for setting timeouts
      - G201 # SQL query construction using format string
      - G202 # SQL query construction using string concatenation
      - G203 # Use of unescaped data in HTML templates
      - G204 # Audit use of command execution
      - G301 # Poor file permissions used when creating a directory
      - G302 # Poor file permissions used with chmod
      - G303 # Creating tempfile using a predictable path
      - G304 # File path provided as taint input
      - G305 # File traversal when extracting zip/tar archive
      - G306 # Poor file permissions used when writing to a new file
      - G307 # Deferring a method which returns an error
      - G401 # Detect the usage of DES, RC4, MD5 or SHA1
      - G402 # Look for bad TLS connection settings
      - G403 # Ensure minimum RSA key length of 2048 bits
      - G404 # Insecure random number source (rand)
      - G501 # Import blocklist: crypto/md5
      - G502 # Import blocklist: crypto/des
      - G503 # Import blocklist: crypto/rc4
      - G504 # Import blocklist: net/http/cgi
      - G505 # Import blocklist: crypto/sha1
      - G601 # Implicit memory aliasing of items from a range statement
    # To specify a set of rules to explicitly exclude.
    # Available rules: https://github.com/securego/gosec#available-rules
    # Default: []
    excludes:
      - G101 # Look for hard coded credentials
      - G102 # Bind to all interfaces
      - G103 # Audit the use of unsafe block
      - G104 # Audit errors not checked
      - G106 # Audit the use of ssh.InsecureIgnoreHostKey
      - G107 # Url provided to HTTP request as taint input
      - G108 # Profiling endpoint automatically exposed on /debug/pprof
      - G109 # Potential Integer overflow made by strconv.Atoi result conversion to int16/32
      - G110 # Potential DoS vulnerability via decompression bomb
      - G111 # Potential directory traversal
      - G112 # Potential slowloris attack
      - G113 # Usage of Rat.SetString in math/big with an overflow (CVE-2022-23772)
      - G114 # Use of net/http serve function that has no support for setting timeouts
      - G201 # SQL query construction using format string
      - G202 # SQL query construction using string concatenation
      - G203 # Use of unescaped data in HTML templates
      - G204 # Audit use of command execution
      - G301 # Poor file permissions used when creating a directory
      - G302 # Poor file permissions used with chmod
      - G303 # Creating tempfile using a predictable path
      - G304 # File path provided as taint input
      - G305 # File traversal when extracting zip/tar archive
      - G306 # Poor file permissions used when writing to a new file
      - G307 # Deferring a method which returns an error
      - G401 # Detect the usage of DES, RC4, MD5 or SHA1
      - G402 # Look for bad TLS connection settings
      - G403 # Ensure minimum RSA key length of 2048 bits
      - G404 # Insecure random number source (rand)
      - G501 # Import blocklist: crypto/md5
      - G502 # Import blocklist: crypto/des
      - G503 # Import blocklist: crypto/rc4
      - G504 # Import blocklist: net/http/cgi
      - G505 # Import blocklist: crypto/sha1
      - G601 # Implicit memory aliasing of items from a range statement
    # Exclude generated files
    # Default: false
    exclude-generated: true
    # Filter out the issues with a lower severity than the given value.
    # Valid options are: low, medium, high.
    # Default: low
    severity: medium
    # Filter out the issues with a lower confidence than the given value.
    # Valid options are: low, medium, high.
    # Default: low
    confidence: medium
    # Concurrency value.
    # Default: the number of logical CPUs usable by the current process.
    concurrency: 12
    # To specify the configuration of rules.
    config:
      # Globals are applicable to all rules.
      global:
        # If true, ignore #nosec in comments (and an alternative as well).
        # Default: false
        nosec: true
        # Add an alternative comment prefix to #nosec (both will work at the same time).
        # Default: ""
        "#nosec": "#my-custom-nosec"
        # Define whether nosec issues are counted as finding or not.
        # Default: false
        show-ignored: true
        # Audit mode enables addition checks that for normal code analysis might be too nosy.
        # Default: false
        audit: true
      G101:
        # Regexp pattern for variables and constants to find.
        # Default: "(?i)passwd|pass|password|pwd|secret|token|pw|apiKey|bearer|cred"
        pattern: "(?i)example"
        # If true, complain about all cases (even with low entropy).
        # Default: false
        ignore_entropy: false
        # Maximum allowed entropy of the string.
        # Default: "80.0"
        entropy_threshold: "80.0"
        # Maximum allowed value of entropy/string length.
        # Is taken into account if entropy >= entropy_threshold/2.
        # Default: "3.0"
        per_char_threshold: "3.0"
        # Calculate entropy for first N chars of the string.
        # Default: "16"
        truncate: "32"
      # Additional functions to ignore while checking unhandled errors.
      # Following functions always ignored:
      #   bytes.Buffer:
      #     - Write
      #     - WriteByte
      #     - WriteRune
      #     - WriteString
      #   fmt:
      #     - Print
      #     - Printf
      #     - Println
      #     - Fprint
      #     - Fprintf
      #     - Fprintln
      #   strings.Builder:
      #     - Write
      #     - WriteByte
      #     - WriteRune
      #     - WriteString
      #   io.PipeWriter:
      #     - CloseWithError
      #   hash.Hash:
      #     - Write
      #   os:
      #     - Unsetenv
      # Default: {}
      G104:
        fmt:
          - Fscanf
      G111:
        # Regexp pattern to find potential directory traversal.
        # Default: "http\\.Dir\\(\"\\/\"\\)|http\\.Dir\\('\\/'\\)"
        pattern: "custom\\.Dir\\(\\)"
      # Maximum allowed permissions mode for os.Mkdir and os.MkdirAll
      # Default: "0750"
      G301: "0750"
      # Maximum allowed permissions mode for os.OpenFile and os.Chmod
      # Default: "0600"
      G302: "0600"
      # Maximum allowed permissions mode for os.WriteFile and ioutil.WriteFile
      # Default: "0600"
      G306: "0600"
```

### gosmopolitan

```yaml
linters-settings:
  gosmopolitan:
    # Allow and ignore `time.Local` usages.
    #
    # Default: false
    allow-time-local: true
    # List of fully qualified names in the `full/pkg/path.name` form, to act as "i18n escape hatches".
    # String literals inside call-like expressions to, or struct literals of those names,
    # are exempt from the writing system check.
    #
    # Default: []
    escape-hatches:
      - 'github.com/nicksnyder/go-i18n/v2/i18n.Message'
      - 'example.com/your/project/i18n/markers.Raw'
      - 'example.com/your/project/i18n/markers.OK'
      - 'example.com/your/project/i18n/markers.TODO'
      - 'command-line-arguments.Simple'
    # Ignore test files.
    #
    # Default: true
    ignore-tests: false
    # List of Unicode scripts to watch for any usage in string literals.
    # https://pkg.go.dev/unicode#pkg-variables
    #
    # Default: ["Han"]
    watch-for-scripts:
      - Devanagari
      - Han
      - Hangul
      - Hiragana
      - Katakana
```

### govet

```yaml
linters-settings:
  govet:
    # Report about shadowed variables.
    # Default: false
    check-shadowing: true
    # Settings per analyzer.
    settings:
      # Analyzer name, run `go tool vet help` to see all analyzers.
      printf:
        # Comma-separated list of print function names to check (in addition to default, see `go tool vet help printf`).
        # Default: []
        funcs:
          - (github.com/golangci/golangci-lint/pkg/logutils.Log).Infof
          - (github.com/golangci/golangci-lint/pkg/logutils.Log).Warnf
          - (github.com/golangci/golangci-lint/pkg/logutils.Log).Errorf
          - (github.com/golangci/golangci-lint/pkg/logutils.Log).Fatalf
      shadow:
        # Whether to be strict about shadowing; can be noisy.
        # Default: false
        strict: true
      unusedresult:
        # Comma-separated list of functions whose results must be used
        # (in addition to defaults context.WithCancel,context.WithDeadline,context.WithTimeout,context.WithValue,
        # errors.New,fmt.Errorf,fmt.Sprint,fmt.Sprintf,sort.Reverse)
        # Default []
        funcs:
          - pkg.MyFunc
        # Comma-separated list of names of methods of type func() string whose results must be used
        # (in addition to default Error,String)
        # Default []
        stringmethods:
          - MyMethod
    # Disable all analyzers.
    # Default: false
    disable-all: true
    # Enable analyzers by name (in addition to default).
    # Run `go tool vet help` to see all analyzers.
    # Default: []
    enable:
      - asmdecl
      - assign
      - atomic
      - atomicalign
      - bools
      - buildtag
      - cgocall
      - composites
      - copylocks
      - deepequalerrors
      - errorsas
      - fieldalignment
      - findcall
      - framepointer
      - httpresponse
      - ifaceassert
      - loopclosure
      - lostcancel
      - nilfunc
      - nilness
      - printf
      - reflectvaluecompare
      - shadow
      - shift
      - sigchanyzer
      - sortslice
      - stdmethods
      - stringintconv
      - structtag
      - testinggoroutine
      - tests
      - unmarshal
      - unreachable
      - unsafeptr
      - unusedresult
      - unusedwrite
    # Enable all analyzers.
    # Default: false
    enable-all: true
    # Disable analyzers by name.
    # Run `go tool vet help` to see all analyzers.
    # Default: []
    disable:
      - asmdecl
      - assign
      - atomic
      - atomicalign
      - bools
      - buildtag
      - cgocall
      - composites
      - copylocks
      - deepequalerrors
      - errorsas
      - fieldalignment
      - findcall
      - framepointer
      - httpresponse
      - ifaceassert
      - loopclosure
      - lostcancel
      - nilfunc
      - nilness
      - printf
      - reflectvaluecompare
      - shadow
      - shift
      - sigchanyzer
      - sortslice
      - stdmethods
      - stringintconv
      - structtag
      - testinggoroutine
      - tests
      - unmarshal
      - unreachable
      - unsafeptr
      - unusedresult
      - unusedwrite
```

### grouper

```yaml
linters-settings:
  grouper:
    # Require the use of a single global 'const' declaration only.
    # Default: false
    const-require-single-const: true
    # Require the use of grouped global 'const' declarations.
    # Default: false
    const-require-grouping: true
    # Require the use of a single 'import' declaration only.
    # Default: false
    import-require-single-import: true
    # Require the use of grouped 'import' declarations.
    # Default: false
    import-require-grouping: true
    # Require the use of a single global 'type' declaration only.
    # Default: false
    type-require-single-type: true
    # Require the use of grouped global 'type' declarations.
    # Default: false
    type-require-grouping: true
    # Require the use of a single global 'var' declaration only.
    # Default: false
    var-require-single-var: true
    # Require the use of grouped global 'var' declarations.
    # Default: false
    var-require-grouping: true
```

### ifshort

```yaml
linters-settings:
  ifshort:
    # Maximum length of variable declaration measured in number of lines, after which linter won't suggest using short syntax.
    # Has higher priority than max-decl-chars.
    # Default: 1
    max-decl-lines: 2
    # Maximum length of variable declaration measured in number of characters, after which linter won't suggest using short syntax.
    # Default: 30
    max-decl-chars: 40
```

### importas

```yaml
linters-settings:
  importas:
    # Do not allow unaliased imports of aliased packages.
    # Default: false
    no-unaliased: true
    # Do not allow non-required aliases.
    # Default: false
    no-extra-aliases: true
    # List of aliases
    # Default: []
    alias:
      # Using `servingv1` alias for `knative.dev/serving/pkg/apis/serving/v1` package.
      - pkg: knative.dev/serving/pkg/apis/serving/v1
        alias: servingv1
      # Using `autoscalingv1alpha1` alias for `knative.dev/serving/pkg/apis/autoscaling/v1alpha1` package.
      - pkg: knative.dev/serving/pkg/apis/autoscaling/v1alpha1
        alias: autoscalingv1alpha1
      # You can specify the package path by regular expression,
      # and alias by regular expression expansion syntax like below.
      # see https://github.com/julz/importas#use-regular-expression for details
      - pkg: knative.dev/serving/pkg/apis/(\w+)/(v[\w\d]+)
        alias: $1$2
```

### interfacebloat

```yaml
linters-settings:
  interfacebloat:
    # The maximum number of methods allowed for an interface.
    # Default: 10
    max: 5
```

### ireturn

```yaml
linters-settings:
  ireturn:
    # ireturn does not allow using `allow` and `reject` settings at the same time.
    # Both settings are lists of the keywords and regular expressions matched to interface or package names.
    # keywords:
    # - `empty` for `interface{}`
    # - `error` for errors
    # - `stdlib` for standard library
    # - `anon` for anonymous interfaces
    # - `generic` for generic interfaces added in go 1.18

    # By default, it allows using errors, empty interfaces, anonymous interfaces,
    # and interfaces provided by the standard library.
    allow:
      - anon
      - error
      - empty
      - stdlib
      # You can specify idiomatic endings for interface
      - (or|er)$
    # reject-list of interfaces
    reject:
      - github.com\/user\/package\/v4\.Type
```

### lll

```yaml
linters-settings:
  lll:
    # Max line length, lines longer will be reported.
    # '\t' is counted as 1 character by default, and can be changed with the tab-width option.
    # Default: 120.
    line-length: 120
    # Tab width in spaces.
    # Default: 1
    tab-width: 1
```

### loggercheck

```yaml
linters-settings:
  loggercheck:
    # Allow check for the github.com/go-kit/log library.
    # Default: true
    kitlog: false
    # Allow check for the k8s.io/klog/v2 library.
    # Default: true
    klog: false
    # Allow check for the github.com/go-logr/logr library.
    # Default: true
    logr: false
    # Allow check for the "sugar logger" from go.uber.org/zap library.
    # Default: true
    zap: false
    # Require all logging keys to be inlined constant strings.
    # Default: false
    require-string-key: true
    # Require printf-like format specifier (%s, %d for example) not present.
    # Default: false
    no-printf-like: true
    # List of custom rules to check against, where each rule is a single logger pattern, useful for wrapped loggers.
    # For example: https://github.com/timonwong/loggercheck/blob/7395ab86595781e33f7afba27ad7b55e6956ebcd/testdata/custom-rules.txt
    # Default: empty
    rules:
      - k8s.io/klog/v2.InfoS # package level exported functions
      - (github.com/go-logr/logr.Logger).Error # "Methods"
      - (*go.uber.org/zap.SugaredLogger).With # Also "Methods", but with a pointer receiver
```

### maintidx

```yaml
linters-settings:
  maintidx:
    # Show functions with maintainability index lower than N.
    # A high index indicates better maintainability (it's kind of the opposite of complexity).
    # Default: 20
    under: 100
```

### makezero

```yaml
linters-settings:
  makezero:
    # Allow only slices initialized with a length of zero.
    # Default: false
    always: true
```

### maligned

```yaml
linters-settings:
  maligned:
    # Print struct with more effective memory layout or not.
    # Default: false
    suggest-new: true
```

### misspell

```yaml
linters-settings:
  misspell:
    # Correct spellings using locale preferences for US or UK.
    # Setting locale to US will correct the British spelling of 'colour' to 'color'.
    # Default is to use a neutral variety of English.
    locale: US
    # Default: []
    ignore-words:
      - someword
```

### musttag

```yaml
linters-settings:
  musttag:
    # A set of custom functions to check in addition to the builtin ones.
    # Default: json, xml, gopkg.in/yaml.v3, BurntSushi/toml, mitchellh/mapstructure
    functions:
      # The full name of the function, including the package.
      - name: github.com/jmoiron/sqlx.Get
        # The struct tag whose presence should be ensured.
        tag: db
        # The position of the argument to check.
        arg-pos: 1
```

### nakedret

```yaml
linters-settings:
  nakedret:
    # Make an issue if func has more lines of code than this setting, and it has naked returns.
    # Default: 30
    max-func-lines: 31
```

### nestif

```yaml
linters-settings:
  nestif:
    # Minimal complexity of if statements to report.
    # Default: 5
    min-complexity: 4
```

### nilnil

```yaml
linters-settings:
  nilnil:
    # Checks that there is no simultaneous return of `nil` error and an invalid value.
    # Default: ["ptr", "func", "iface", "map", "chan"]
    checked-types:
      - ptr
      - func
      - iface
      - map
      - chan
```

### nlreturn

```yaml
linters-settings:
  nlreturn:
    # Size of the block (including return statement that is still "OK")
    # so no return split required.
    # Default: 1
    block-size: 2
```

### nolintlint

```yaml
linters-settings:
  nolintlint:
    # Disable to ensure that all nolint directives actually have an effect.
    # Default: false
    allow-unused: true
    # Exclude following linters from requiring an explanation.
    # Default: []
    allow-no-explanation: []
    # Enable to require an explanation of nonzero length after each nolint directive.
    # Default: false
    require-explanation: true
    # Enable to require nolint directives to mention the specific linter being suppressed.
    # Default: false
    require-specific: true
```

### nonamedreturns

```yaml
linters-settings:
  nonamedreturns:
    # Report named error if it is assigned inside defer.
    # Default: false
    report-error-in-defer: true
```

### paralleltest

```yaml
linters-settings:
  paralleltest:
    # Ignore missing calls to `t.Parallel()` and only report incorrect uses of it.
    # Default: false
    ignore-missing: true
```

### prealloc

```yaml
linters-settings:
  prealloc:
    # IMPORTANT: we don't recommend using this linter before doing performance profiling.
    # For most programs usage of prealloc will be a premature optimization.

    # Report pre-allocation suggestions only on simple loops that have no returns/breaks/continues/gotos in them.
    # Default: true
    simple: false
    # Report pre-allocation suggestions on range loops.
    # Default: true
    range-loops: false
    # Report pre-allocation suggestions on for loops.
    # Default: false
    for-loops: true
```

### predeclared

```yaml
linters-settings:
  predeclared:
    # Comma-separated list of predeclared identifiers to not report on.
    # Default: ""
    ignore: "new,int"
    # Include method names and field names (i.e., qualified names) in checks.
    # Default: false
    q: true
```

### promlinter

```yaml
linters-settings:
  promlinter:
    # Promlinter cannot infer all metrics name in static analysis.
    # Enable strict mode will also include the errors caused by failing to parse the args.
    # Default: false
    strict: true
    # Please refer to https://github.com/yeya24/promlinter#usage for detailed usage.
    # Default: []
    disabled-linters:
      - Help
      - MetricUnits
      - Counter
      - HistogramSummaryReserved
      - MetricTypeInName
      - ReservedChars
      - CamelCase
      - UnitAbbreviations
```

### reassign

```yaml
linters-settings:
  reassign:
    # Patterns for global variable names that are checked for reassignment.
    # See https://github.com/curioswitch/go-reassign#usage
    # Default: ["EOF", "Err.*"]
    patterns:
      - ".*"
```

### revive

```yaml
linters-settings:
  revive:
    # Maximum number of open files at the same time.
    # See https://github.com/mgechev/revive#command-line-flags
    # Defaults to unlimited.
    max-open-files: 2048
    # When set to false, ignores files with "GENERATED" header, similar to golint.
    # See https://github.com/mgechev/revive#available-rules for details.
    # Default: false
    ignore-generated-header: true
    # Sets the default severity.
    # See https://github.com/mgechev/revive#configuration
    # Default: warning
    severity: error
    # Enable all available rules.
    # Default: false
    enable-all-rules: true
    # Sets the default failure confidence.
    # This means that linting errors with less than 0.8 confidence will be ignored.
    # Default: 0.8
    confidence: 0.1
    rules:
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#add-constant
      - name: add-constant
        severity: warning
        disabled: false
        arguments:
          - maxLitCount: "3"
            allowStrs: '""'
            allowInts: "0,1,2"
            allowFloats: "0.0,0.,1.0,1.,2.0,2."
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#argument-limit
      - name: argument-limit
        severity: warning
        disabled: false
        arguments: [4]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#atomic
      - name: atomic
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#banned-characters
      - name: banned-characters
        severity: warning
        disabled: false
        arguments: ["Ω", "Σ", "σ", "7"]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#bare-return
      - name: bare-return
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#blank-imports
      - name: blank-imports
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#bool-literal-in-expr
      - name: bool-literal-in-expr
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#call-to-gc
      - name: call-to-gc
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#cognitive-complexity
      - name: cognitive-complexity
        severity: warning
        disabled: false
        arguments: [7]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#comment-spacings
      - name: comment-spacings
        severity: warning
        disabled: false
        arguments:
          - mypragma
          - otherpragma
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#confusing-naming
      - name: confusing-naming
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#confusing-results
      - name: confusing-results
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#constant-logical-expr
      - name: constant-logical-expr
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#context-as-argument
      - name: context-as-argument
        severity: warning
        disabled: false
        arguments:
          - allowTypesBefore: "*testing.T,*github.com/user/repo/testing.Harness"
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#context-keys-type
      - name: context-keys-type
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#cyclomatic
      - name: cyclomatic
        severity: warning
        disabled: false
        arguments: [3]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#datarace
      - name: datarace
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#deep-exit
      - name: deep-exit
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#defer
      - name: defer
        severity: warning
        disabled: false
        arguments:
          - ["call-chain", "loop"]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#dot-imports
      - name: dot-imports
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#duplicated-imports
      - name: duplicated-imports
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#early-return
      - name: early-return
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#empty-block
      - name: empty-block
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#empty-lines
      - name: empty-lines
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#error-naming
      - name: error-naming
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#error-return
      - name: error-return
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#error-strings
      - name: error-strings
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#errorf
      - name: errorf
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#exported
      - name: exported
        severity: warning
        disabled: false
        arguments:
          - "checkPrivateReceivers"
          - "sayRepetitiveInsteadOfStutters"
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#file-header
      - name: file-header
        severity: warning
        disabled: false
        arguments:
          - This is the text that must appear at the top of source files.
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#flag-parameter
      - name: flag-parameter
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#function-result-limit
      - name: function-result-limit
        severity: warning
        disabled: false
        arguments: [2]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#function-length
      - name: function-length
        severity: warning
        disabled: false
        arguments: [10, 0]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#get-return
      - name: get-return
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#identical-branches
      - name: identical-branches
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#if-return
      - name: if-return
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#increment-decrement
      - name: increment-decrement
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#indent-error-flow
      - name: indent-error-flow
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#imports-blacklist
      - name: imports-blacklist
        severity: warning
        disabled: false
        arguments:
          - "crypto/md5"
          - "crypto/sha1"
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#import-shadowing
      - name: import-shadowing
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#line-length-limit
      - name: line-length-limit
        severity: warning
        disabled: false
        arguments: [80]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#max-public-structs
      - name: max-public-structs
        severity: warning
        disabled: false
        arguments: [3]
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#modifies-parameter
      - name: modifies-parameter
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#modifies-value-receiver
      - name: modifies-value-receiver
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#nested-structs
      - name: nested-structs
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#optimize-operands-order
      - name: optimize-operands-order
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#package-comments
      - name: package-comments
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#range
      - name: range
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#range-val-in-closure
      - name: range-val-in-closure
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#range-val-address
      - name: range-val-address
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#receiver-naming
      - name: receiver-naming
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#redefines-builtin-id
      - name: redefines-builtin-id
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#string-of-int
      - name: string-of-int
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#string-format
      - name: string-format
        severity: warning
        disabled: false
        arguments:
          - - 'core.WriteError[1].Message'
            - '/^([^A-Z]|$)/'
            - must not start with a capital letter
          - - 'fmt.Errorf[0]'
            - '/(^|[^\.!?])$/'
            - must not end in punctuation
          - - panic
            - '/^[^\n]*$/'
            - must not contain line breaks
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#struct-tag
      - name: struct-tag
        arguments:
          - "json,inline"
          - "bson,outline,gnu"
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#superfluous-else
      - name: superfluous-else
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#time-equal
      - name: time-equal
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#time-naming
      - name: time-naming
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#var-naming
      - name: var-naming
        severity: warning
        disabled: false
        arguments:
          - ["ID"] # AllowList
          - ["VM"] # DenyList
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#var-declaration
      - name: var-declaration
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unconditional-recursion
      - name: unconditional-recursion
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unexported-naming
      - name: unexported-naming
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unexported-return
      - name: unexported-return
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unhandled-error
      - name: unhandled-error
        severity: warning
        disabled: false
        arguments:
          - "fmt.Printf"
          - "myFunction"
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unnecessary-stmt
      - name: unnecessary-stmt
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unreachable-code
      - name: unreachable-code
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unused-parameter
      - name: unused-parameter
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#unused-receiver
      - name: unused-receiver
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#useless-break
      - name: useless-break
        severity: warning
        disabled: false
      # https://github.com/mgechev/revive/blob/master/RULES_DESCRIPTIONS.md#waitgroup-by-value
      - name: waitgroup-by-value
        severity: warning
        disabled: false
```

### rowserrcheck

```yaml
linters-settings:
  rowserrcheck:
    # database/sql is always checked
    # Default: []
    packages:
      - github.com/jmoiron/sqlx
```

### staticcheck

```yaml
linters-settings:
  staticcheck:
    # Deprecated: use the global `run.go` instead.
    go: "1.15"
    # SAxxxx checks in https://staticcheck.io/docs/configuration/options/#checks
    # Default: ["*"]
    checks: ["all"]
```

### stylecheck

```yaml
linters-settings:
  stylecheck:
    # Deprecated: use the global `run.go` instead.
    go: "1.15"
    # STxxxx checks in https://staticcheck.io/docs/configuration/options/#checks
    # Default: ["*"]
    checks: ["all", "-ST1000", "-ST1003", "-ST1016", "-ST1020", "-ST1021", "-ST1022"]
    # https://staticcheck.io/docs/configuration/options/#dot_import_whitelist
    # Default: ["github.com/mmcloughlin/avo/build", "github.com/mmcloughlin/avo/operand", "github.com/mmcloughlin/avo/reg"]
    dot-import-whitelist:
      - fmt
    # https://staticcheck.io/docs/configuration/options/#initialisms
    # Default: ["ACL", "API", "ASCII", "CPU", "CSS", "DNS", "EOF", "GUID", "HTML", "HTTP", "HTTPS", "ID", "IP", "JSON", "QPS", "RAM", "RPC", "SLA", "SMTP", "SQL", "SSH", "TCP", "TLS", "TTL", "UDP", "UI", "GID", "UID", "UUID", "URI", "URL", "UTF8", "VM", "XML", "XMPP", "XSRF", "XSS", "SIP", "RTP", "AMQP", "DB", "TS"]
    initialisms: ["ACL", "API", "ASCII", "CPU", "CSS", "DNS", "EOF", "GUID", "HTML", "HTTP", "HTTPS", "ID", "IP", "JSON", "QPS", "RAM", "RPC", "SLA", "SMTP", "SQL", "SSH", "TCP", "TLS", "TTL", "UDP", "UI", "GID", "UID", "UUID", "URI", "URL", "UTF8", "VM", "XML", "XMPP", "XSRF", "XSS", "SIP", "RTP", "AMQP", "DB", "TS"]
    # https://staticcheck.io/docs/configuration/options/#http_status_code_whitelist
    # Default: ["200", "400", "404", "500"]
    http-status-code-whitelist: ["200", "400", "404", "500"]
```

### tagalign

```yaml
linters-settings:
  tagalign:
    # Align and sort can be used together or separately.
    #
    # Whether enable align. If true, the struct tags will be aligned.
    # eg:
    # type FooBar struct {
    #     Bar    string `json:"bar" validate:"required"`
    #     FooFoo int8   `json:"foo_foo" validate:"required"`
    # }
    # will be formatted to:
    # type FooBar struct {
    #     Bar    string `json:"bar"     validate:"required"`
    #     FooFoo int8   `json:"foo_foo" validate:"required"`
    # }
    # Default: true.
    align: false
    # Whether enable tags sort.
    # If true, the tags will be sorted by name in ascending order.
    # eg: `xml:"bar" json:"bar" validate:"required"` -> `json:"bar" validate:"required" xml:"bar"`
    # Default: true
    sort: false
    # Specify the order of tags, the other tags will be sorted by name.
    # This option will be ignored if `sort` is false.
    # Default: []
    order:
      - json
      - yaml
      - yml
      - toml
      - mapstructure
      - binding
      - validate
```

### tagliatelle

```yaml
linters-settings:
  tagliatelle:
    # Check the struct tag name case.
    case:
      # Use the struct field name to check the name of the struct tag.
      # Default: false
      use-field-name: true
      # `camel` is used for `json` and `yaml`, and `header` is used for `header` (can be overridden)
      # Default: {}
      rules:
        # Any struct tag type can be used.
        # Support string case: `camel`, `pascal`, `kebab`, `snake`, `goCamel`, `goPascal`, `goKebab`, `goSnake`, `upper`, `lower`, `header`
        json: camel
        yaml: camel
        xml: camel
        bson: camel
        avro: snake
        mapstructure: kebab
```

### tenv

```yaml
linters-settings:
  tenv:
    # The option `all` will run against whole test files (`_test.go`) regardless of method/function signatures.
    # Otherwise, only methods that take `*testing.T`, `*testing.B`, and `testing.TB` as arguments are checked.
    # Default: false
    all: false
```

### testpackage

```yaml
linters-settings:
  testpackage:
    # Regexp pattern to skip files.
    # Default: "(export|internal)_test\\.go"
    skip-regexp: (export|internal)_test\.go
    # List of packages that don't end with _test that tests are allowed to be in.
    # Default: "main"
    allow-packages:
      - example
      - main
```

### thelper

```yaml
linters-settings:
  thelper:
    test:
      # Check *testing.T is first param (or after context.Context) of helper function.
      # Default: true
      first: false
      # Check *testing.T param has name t.
      # Default: true
      name: false
      # Check t.Helper() begins helper function.
      # Default: true
      begin: false
    benchmark:
      # Check *testing.B is first param (or after context.Context) of helper function.
      # Default: true
      first: false
      # Check *testing.B param has name b.
      # Default: true
      name: false
      # Check b.Helper() begins helper function.
      # Default: true
      begin: false
    tb:
      # Check *testing.TB is first param (or after context.Context) of helper function.
      # Default: true
      first: false
      # Check *testing.TB param has name tb.
      # Default: true
      name: false
      # Check tb.Helper() begins helper function.
      # Default: true
      begin: false
    fuzz:
      # Check *testing.F is first param (or after context.Context) of helper function.
      # Default: true
      first: false
      # Check *testing.F param has name f.
      # Default: true
      name: false
      # Check f.Helper() begins helper function.
      # Default: true
      begin: false
```

### usestdlibvars

```yaml
linters-settings:
  usestdlibvars:
    # Suggest the use of http.MethodXX.
    # Default: true
    http-method: false
    # Suggest the use of http.StatusXX.
    # Default: true
    http-status-code: false
    # Suggest the use of time.Weekday.String().
    # Default: true
    time-weekday: true
    # Suggest the use of time.Month.String().
    # Default: false
    time-month: true
    # Suggest the use of time.Layout.
    # Default: false
    time-layout: true
    # Suggest the use of crypto.Hash.String().
    # Default: false
    crypto-hash: true
    # Suggest the use of rpc.DefaultXXPath.
    # Default: false
    default-rpc-path: true
    # DEPRECATED Suggest the use of os.DevNull.
    # Default: false
    os-dev-null: true
    # Suggest the use of sql.LevelXX.String().
    # Default: false
    sql-isolation-level: true
    # Suggest the use of tls.SignatureScheme.String().
    # Default: false
    tls-signature-scheme: true
    # Suggest the use of constant.Kind.String().
    # Default: false
    constant-kind: true
    # DEPRECATED Suggest the use of syslog.Priority.
    # Default: false
    syslog-priority: true
```

### unparam

```yaml
linters-settings:
  unparam:
    # Inspect exported functions.
    #
    # Set to true if no external program/library imports your code.
    # XXX: if you enable this setting, unparam will report a lot of false-positives in text editors:
    # if it's called for subdir of a project it can't find external interfaces. All text editor integrations
    # with golangci-lint call it on a directory with the changed file.
    #
    # Default: false
    check-exported: true
```

### varcheck

```yaml
linters-settings:
  varcheck:
    # Check usage of exported fields and variables.
    # Default: false
    exported-fields: true
```

### varnamelen

```yaml
linters-settings:
  varnamelen:
    # The longest distance, in source lines, that is being considered a "small scope".
    # Variables used in at most this many lines will be ignored.
    # Default: 5
    max-distance: 6
    # The minimum length of a variable's name that is considered "long".
    # Variable names that are at least this long will be ignored.
    # Default: 3
    min-name-length: 2
    # Check method receivers.
    # Default: false
    check-receiver: true
    # Check named return values.
    # Default: false
    check-return: true
    # Check type parameters.
    # Default: false
    check-type-param: true
    # Ignore "ok" variables that hold the bool return value of a type assertion.
    # Default: false
    ignore-type-assert-ok: true
    # Ignore "ok" variables that hold the bool return value of a map index.
    # Default: false
    ignore-map-index-ok: true
    # Ignore "ok" variables that hold the bool return value of a channel receive.
    # Default: false
    ignore-chan-recv-ok: true
    # Optional list of variable names that should be ignored completely.
    # Default: []
    ignore-names:
      - err
    # Optional list of variable declarations that should be ignored completely.
    # Entries must be in one of the following forms (see below for examples):
    # - for variables, parameters, named return values, method receivers, or type parameters:
    #   <name> <type>  (<type> can also be a pointer/slice/map/chan/...)
    # - for constants: const <name>
    #
    # Default: []
    ignore-decls:
      - c echo.Context
      - t testing.T
      - f *foo.Bar
      - e error
      - i int
      - const C
      - T any
      - m map[string]int
```

### whitespace

```yaml
linters-settings:
  whitespace:
    # Enforces newlines (or comments) after every multi-line if statement.
    # Default: false
    multi-if: true
    # Enforces newlines (or comments) after every multi-line function signature.
    # Default: false
    multi-func: true
```

### wrapcheck

```yaml
linters-settings:
  wrapcheck:
    # An array of strings that specify substrings of signatures to ignore.
    # If this set, it will override the default set of ignored signatures.
    # See https://github.com/tomarrell/wrapcheck#configuration for more information.
    # Default: [".Errorf(", "errors.New(", "errors.Unwrap(", ".Wrap(", ".Wrapf(", ".WithMessage(", ".WithMessagef(", ".WithStack("]
    ignoreSigs:
      - .Errorf(
      - errors.New(
      - errors.Unwrap(
      - .Wrap(
      - .Wrapf(
      - .WithMessage(
      - .WithMessagef(
      - .WithStack(
    # An array of strings that specify regular expressions of signatures to ignore.
    # Default: []
    ignoreSigRegexps:
      - \.New.*Error\(
    # An array of strings that specify globs of packages to ignore.
    # Default: []
    ignorePackageGlobs:
      - encoding/*
      - github.com/pkg/*
    # An array of strings that specify regular expressions of interfaces to ignore.
    # Default: []
    ignoreInterfaceRegexps:
      - ^(?i)c(?-i)ach(ing|e)
```

### wsl

```yaml
linters-settings:
  wsl:
    # See https://github.com/bombsimon/wsl/blob/master/doc/configuration.md for documentation of available settings.
    # These are the defaults for `golangci-lint`.

    # Do strict checking when assigning from append (x = append(x, y)). If
    # this is set to true - the append call must append either a variable
    # assigned, called or used on the line above.
    strict-append: true
    # Allows assignments to be cuddled with variables used in calls on
    # line above and calls to be cuddled with assignments of variables
    # used in call on line above.
    allow-assign-and-call: true
    # Allows assignments to be cuddled with anything.
    allow-assign-and-anything: false
    # Allows cuddling to assignments even if they span over multiple lines.
    allow-multiline-assign: true
    # If the number of lines in a case block is equal to or lager than this
    # number, the case *must* end white a newline.
    force-case-trailing-whitespace: 0
    # Allow blocks to end with comments.
    allow-trailing-comment: false
    # Allow multiple comments in the beginning of a block separated with newline.
    allow-separated-leading-comment: false
    # Allow multiple var/declaration statements to be cuddled.
    allow-cuddle-declarations: false
    # A list of call idents that everything can be cuddled with.
    # Defaults to calls looking like locks.
    allow-cuddle-with-calls: ["Lock", "RLock"]
    # AllowCuddleWithRHS is a list of right hand side variables that is allowed
    # to be cuddled with anything. Defaults to assignments or calls looking
    # like unlocks.
    allow-cuddle-with-rhs: ["Unlock", "RUnlock"]
    # Causes an error when an If statement that checks an error variable doesn't
    # cuddle with the assignment of that variable.
    force-err-cuddling: false
    # When force-err-cuddling is enabled this is a list of names
    # used for error variables to check for in the conditional.
    error-variable-names: ["err"]
    # Causes an error if a short declaration (:=) cuddles with anything other than
    # another short declaration.
    # This logic overrides force-err-cuddling among others.
    force-short-decl-cuddling: false
```

### custom

```yaml
linters-settings:
  # The custom section can be used to define linter plugins to be loaded at runtime.
  # See README documentation for more info.
  custom:
    # Each custom linter should have a unique name.
    example:
      # The path to the plugin *.so. Can be absolute or local.
      # Required for each custom linter.
      path: /path/to/example.so
      # The description of the linter.
      # Optional.
      description: This is an example usage of a plugin linter.
      # Intended to point to the repo location of the linter.
      # Optional.
      original-url: github.com/golangci/example-linter
```