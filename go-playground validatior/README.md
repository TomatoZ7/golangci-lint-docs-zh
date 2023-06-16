Package validator
=================
<img align="right" src="https://raw.githubusercontent.com/go-playground/validator/v10/logo.png">[![Join the chat at https://gitter.im/go-playground/validator](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/go-playground/validator?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
![Project status](https://img.shields.io/badge/version-10.14.1-green.svg)
[![Build Status](https://travis-ci.org/go-playground/validator.svg?branch=master)](https://travis-ci.org/go-playground/validator)
[![Coverage Status](https://coveralls.io/repos/go-playground/validator/badge.svg?branch=master&service=github)](https://coveralls.io/github/go-playground/validator?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/go-playground/validator)](https://goreportcard.com/report/github.com/go-playground/validator)
[![GoDoc](https://godoc.org/github.com/go-playground/validator?status.svg)](https://pkg.go.dev/github.com/go-playground/validator/v10)
![License](https://img.shields.io/dub/l/vibe-d.svg)

validator 包根据 tags 对结构体和单个字段进行值验证。

它具有以下这些**独特**的功能：

- 使用验证 tag 或自定义验证器进行跨字段和跨结构体验证；
- 深入 Slice, Array 和 Map，可以对任何或所有级别的多维字段进行验证；
- 具备深入验证 map 的建和值的能力；
- 在验证接口类型前会先确定它的底层数据类型；
- 能够处理自定义字段类型例如 sql 驱动程序 [Valuer](https://golang.org/src/database/sql/driver/types.go?s=1210:1293#L29)；
- 支持 tag 别名，允许将多个验证规则映射到单个 tag，以便能够更简单地在结构体上定义验证规则；
- 在进行验证操作时，可以指定提取自定义的字段名。例如，可以在验证过程中指定提取 JSON 名称，并在生成的验证错误结果（FieldError）中将其作为可用信息；
- 可以自定义并支持国际化（i18n）的错误信息；
- 是 [gin](https://github.com/gin-gonic/gin) 框架的默认验证器，在 gin 中从 v8 升级到 v9 可以查阅[这里](https://github.com/go-playground/validator/tree/master/_examples/gin-upgrading-overriding)。


## Installation

使用 `go get`：

```sh
go get github.com/go-playground/validator/v10
```

然后在你的源码中引入 `validator` 包：

```go
import "github.com/go-playground/validator/v10"
```


## Error Return Value

验证函数返回 error 类型。

它们返回 error 类型是为了避免下面讨论的 issue，其中 err 始终 != nil：

* http://stackoverflow.com/a/29138676/3158232
* https://github.com/go-playground/validator/issues/134

当输入的验证规则错误时，validator 只返回 InvalidValidationError，而对于有效的验证规则输入则返回 nil 或 ValidationErrors；所以，在你的代码中你只需要去检查返回的 error 是否为 nil，如果不是，则进一步检查 error 是否为 InvalidValidationError（大多数情况下不是）并将其强制转为 ValidationErrors 类型，就像这样：

```go
err := validate.Struct(mystruct)
validationErrors := err.(validator.ValidationErrors)
```


## Usage and documentation

请参阅 [https://pkg.go.dev/github.com/go-playground/validator/v10](https://pkg.go.dev/github.com/go-playground/validator/v10) 获取详细的使用文档。

### 案例:

- [简单使用](https://github.com/go-playground/validator/blob/master/_examples/simple/main.go)
- [自定义字段类型](https://github.com/go-playground/validator/blob/master/_examples/custom/main.go)
- [多维结构体](https://github.com/go-playground/validator/blob/master/_examples/struct-level/main.go)
- [翻译和自定义错误](https://github.com/go-playground/validator/blob/master/_examples/translations/main.go)
- [Gin 升级 和/或 覆盖验证器](https://github.com/go-playground/validator/tree/v9/_examples/gin-upgrading-overriding)
- [wash - 一个把所有内容组合在一起的示例应用程序](https://github.com/bluesuncorp/wash)

## 内置的验证规则

### Fields:

| Tag | Description |
| - | - |
| eqcsfield | 字段等于另一个字段（相对，可以跨结构体）|
| eqfield | 字段等于另一个字段 |
| fieldcontains | 检查指定字符是否存在于字段中 |
| fieldexcludes | 检查指定字符是否不存在于字段中 |
| gtcsfield | 当前字段大于指定相关字段 |
| gtecsfield | 当前字段大于等于指定相关字段 |
| gtefield | 当前字段大于等于指定字段 |
| gtfield | 当前字段大于指定字段 |
| ltcsfield | 当前字段小于指定相关字段 |
| ltecsfield | 当前字段小于等于指定相关字段 |
| ltefield | 当前字段小于等于指定字段 |
| ltfield | 当前字段小于指定字段 |
| necsfield | 当前字段不等于指定字段（相对） |
| nefield | 当前字段不等于指定字段 |

### Network:

| Tag | Description |
| - | - |
| cidr | Classless Inter-Domain Routing CIDR（无类别域间路由） |
| cidrv4 | Classless Inter-Domain Routing CIDRv4 |
| cidrv6 | Classless Inter-Domain Routing CIDRv6 |
| datauri | Data URL |
| fqdn | 完全限定域名 (FQDN) |
| hostname | Hostname RFC 952 |
| hostname_port | 主机端口 |
| hostname_rfc1123 | Hostname RFC 1123 |
| ip | 互联网协议地址 IP |
| ip4_addr | 互联网协议地址 IPv4（只验证格式，下同） |
| ip6_addr | 互联网协议地址 IPv6 |
| ip_addr | 互联网协议地址 IP |
| ipv4 | 互联网协议地址 IPv4（验证格式和地址有效性，下同） |
| ipv6 | 互联网协议地址 IPv6 |
| mac | 媒体访问控制地址 MAC |
| tcp4_addr | TCP 地址 TCPv4 |
| tcp6_addr | TCP 地址 TCPv6 |
| tcp_addr | TCP 地址 |
| udp4_addr | UDP 地址 UDPv4 |
| udp6_addr | UDP 地址 UDPv6 |
| udp_addr | UDP 地址 UDP |
| unix_addr | Unix domain socket end point Address |
| uri | URI String |
| url | URL String |
| http_url | HTTP URL String |
| url_encoded | URL Encoded |
| urn_rfc2141 | Urn RFC 2141 String |

### Strings:

| Tag | Description |
| - | - |
| alpha | 仅限字母 |
| alphanum | 字幕数字 |
| alphanumunicode | 字母数字和 Unicode |
| alphaunicode | 字母和 Unicode |
| ascii | ASCII |
| boolean | Boolean |
| contains | Contains |
| containsany | Contains Any |
| containsrune | Contains Rune |
| endsnotwith | Ends Not With |
| endswith | Ends With |
| excludes | Excludes 排除 |
| excludesall | Excludes All |
| excludesrune | Excludes Rune |
| lowercase | 小写 |
| multibyte | 多字节字符 |
| number | Number |
| numeric | Numeric |
| printascii | 可打印的 ASCII |
| startsnotwith | Starts Not With |
| startswith | Starts With |
| uppercase | 大写 |

### Format:
| Tag | Description |
| - | - |
| base64 | Base64 String |
| base64url | Base64URL String |
| base64rawurl | Base64RawURL String |
| bic | 企业识别码 (ISO 9362) |
| bcp47_language_tag | Language tag (BCP 47) |
| btc_addr | 比特币地址 |
| btc_addr_bech32 | Bitcoin Bech32 Address (segwit) |
| credit_card | 信用卡号 |
| mongodb | MongoDB ObjectID |
| cron | Cron |
| datetime | Datetime |
| e164 | e164 formatted phone number |
| email | E-mail String |
| eth_addr | 以太坊地址 |
| hexadecimal | 16 进制字符串 |
| hexcolor | 16 进制色码字符串 |
| hsl | HSL String |
| hsla | HSLA String |
| html | HTML Tags |
| html_encoded | HTML Encoded |
| isbn | 国际标准书号 |
| isbn10 | 国际标准图书编号 10 |
| isbn13 | 国际标准图书编号 13 |
| iso3166_1_alpha2 | 两个字母的国家代码 (ISO 3166-1 alpha-2) (ISO 3166-1 alpha-2) |
| iso3166_1_alpha3 | 三个字母的国家代码 (ISO 3166-1 alpha-3) |
| iso3166_1_alpha_numeric | 数字国家代码 (ISO 3166-1 numeric) |
| iso3166_2 | 国家行政区划代码 (ISO 3166-2) |
| iso4217 | 货币代码 (ISO 4217) |
| json | JSON |
| jwt | JSON Web Token (JWT) |
| latitude | 纬度 |
| longitude | 经度 |
| luhn_checksum | Luhn Algorithm Checksum (for strings and (u)int) |
| postcode_iso3166_alpha2 | 邮政编码 |
| postcode_iso3166_alpha2_field | 邮政编码 |
| rgb | RGB String |
| rgba | RGBA String |
| ssn | 社会保险号 SSN |
| timezone | 时区 |
| uuid | Universally Unique Identifier UUID |
| uuid3 | Universally Unique Identifier UUID v3 |
| uuid3_rfc4122 | Universally Unique Identifier UUID v3 RFC4122 |
| uuid4 | Universally Unique Identifier UUID v4 |
| uuid4_rfc4122 | Universally Unique Identifier UUID v4 RFC4122 |
| uuid5 | Universally Unique Identifier UUID v5 |
| uuid5_rfc4122 | Universally Unique Identifier UUID v5 RFC4122 |
| uuid_rfc4122 | Universally Unique Identifier UUID RFC4122 |
| md4 | MD4 hash |
| md5 | MD5 hash |
| sha256 | SHA256 hash |
| sha384 | SHA384 hash |
| sha512 | SHA512 hash |
| ripemd128 | RIPEMD-128 hash |
| ripemd128 | RIPEMD-160 hash |
| tiger128 | TIGER128 hash |
| tiger160 | TIGER160 hash |
| tiger192 | TIGER192 hash |
| semver | Semantic Versioning 2.0.0 |
| ulid | Universally Unique Lexicographically Sortable Identifier ULID |
| cve | Common Vulnerabilities and Exposures Identifier (CVE id) |

### Comparisons:
| Tag | Description |
| - | - |
| eq | 等于 |
| eq_ignore_case | 等于，忽略大小写 |
| gt | 大于 |
| gte | 大于等于 |
| lt | 小于 |
| lte | 小于等于 |
| ne | 不等于 |
| ne_ignore_case | 不等于，忽略大小写 |

### Other:
| Tag | Description |
| - | - |
| dir | Existing Directory |
| dirpath | 目录路径 |
| file | Existing File |
| filepath | 文件路径 |
| image | Image |
| isdefault | Is Default |
| len | Length |
| max | Maximum |
| min | Minimum |
| oneof | One Of |
| required | Required |
| required_if | Required If |
| required_unless | Required Unless |
| required_with | Required With |
| required_with_all | Required With All |
| required_without | Required Without |
| required_without_all | Required Without All |
| excluded_if | Excluded If |
| excluded_unless | Excluded Unless |
| excluded_with | Excluded With |
| excluded_with_all | Excluded With All |
| excluded_without | Excluded Without |
| excluded_without_all | Excluded Without All |
| unique | Unique |

#### Aliases:
| Tag | Description |
| - | - |
| iscolor | hexcolor\|rgb\|rgba\|hsl\|hsla |
| country_code | iso3166_1_alpha2\|iso3166_1_alpha3\|iso3166_1_alpha_numeric |

## Benchmarks

### Run on MacBook Pro (15-inch, 2017) go version go1.10.2 darwin/amd64

```go
goos: darwin
goarch: amd64
pkg: github.com/go-playground/validator
BenchmarkFieldSuccess-8                                         20000000                83.6 ns/op             0 B/op          0 allocs/op
BenchmarkFieldSuccessParallel-8                                 50000000                26.8 ns/op             0 B/op          0 allocs/op
BenchmarkFieldFailure-8                                          5000000               291 ns/op             208 B/op          4 allocs/op
BenchmarkFieldFailureParallel-8                                 20000000               107 ns/op             208 B/op          4 allocs/op
BenchmarkFieldArrayDiveSuccess-8                                 2000000               623 ns/op             201 B/op         11 allocs/op
BenchmarkFieldArrayDiveSuccessParallel-8                        10000000               237 ns/op             201 B/op         11 allocs/op
BenchmarkFieldArrayDiveFailure-8                                 2000000               859 ns/op             412 B/op         16 allocs/op
BenchmarkFieldArrayDiveFailureParallel-8                         5000000               335 ns/op             413 B/op         16 allocs/op
BenchmarkFieldMapDiveSuccess-8                                   1000000              1292 ns/op             432 B/op         18 allocs/op
BenchmarkFieldMapDiveSuccessParallel-8                           3000000               467 ns/op             432 B/op         18 allocs/op
BenchmarkFieldMapDiveFailure-8                                   1000000              1082 ns/op             512 B/op         16 allocs/op
BenchmarkFieldMapDiveFailureParallel-8                           5000000               425 ns/op             512 B/op         16 allocs/op
BenchmarkFieldMapDiveWithKeysSuccess-8                           1000000              1539 ns/op             480 B/op         21 allocs/op
BenchmarkFieldMapDiveWithKeysSuccessParallel-8                   3000000               613 ns/op             480 B/op         21 allocs/op
BenchmarkFieldMapDiveWithKeysFailure-8                           1000000              1413 ns/op             721 B/op         21 allocs/op
BenchmarkFieldMapDiveWithKeysFailureParallel-8                   3000000               575 ns/op             721 B/op         21 allocs/op
BenchmarkFieldCustomTypeSuccess-8                               10000000               216 ns/op              32 B/op          2 allocs/op
BenchmarkFieldCustomTypeSuccessParallel-8                       20000000                82.2 ns/op            32 B/op          2 allocs/op
BenchmarkFieldCustomTypeFailure-8                                5000000               274 ns/op             208 B/op          4 allocs/op
BenchmarkFieldCustomTypeFailureParallel-8                       20000000               116 ns/op             208 B/op          4 allocs/op
BenchmarkFieldOrTagSuccess-8                                     2000000               740 ns/op              16 B/op          1 allocs/op
BenchmarkFieldOrTagSuccessParallel-8                             3000000               474 ns/op              16 B/op          1 allocs/op
BenchmarkFieldOrTagFailure-8                                     3000000               471 ns/op             224 B/op          5 allocs/op
BenchmarkFieldOrTagFailureParallel-8                             3000000               414 ns/op             224 B/op          5 allocs/op
BenchmarkStructLevelValidationSuccess-8                         10000000               213 ns/op              32 B/op          2 allocs/op
BenchmarkStructLevelValidationSuccessParallel-8                 20000000                91.8 ns/op            32 B/op          2 allocs/op
BenchmarkStructLevelValidationFailure-8                          3000000               473 ns/op             304 B/op          8 allocs/op
BenchmarkStructLevelValidationFailureParallel-8                 10000000               234 ns/op             304 B/op          8 allocs/op
BenchmarkStructSimpleCustomTypeSuccess-8                         5000000               385 ns/op              32 B/op          2 allocs/op
BenchmarkStructSimpleCustomTypeSuccessParallel-8                10000000               161 ns/op              32 B/op          2 allocs/op
BenchmarkStructSimpleCustomTypeFailure-8                         2000000               640 ns/op             424 B/op          9 allocs/op
BenchmarkStructSimpleCustomTypeFailureParallel-8                 5000000               318 ns/op             440 B/op         10 allocs/op
BenchmarkStructFilteredSuccess-8                                 2000000               597 ns/op             288 B/op          9 allocs/op
BenchmarkStructFilteredSuccessParallel-8                        10000000               266 ns/op             288 B/op          9 allocs/op
BenchmarkStructFilteredFailure-8                                 3000000               454 ns/op             256 B/op          7 allocs/op
BenchmarkStructFilteredFailureParallel-8                        10000000               214 ns/op             256 B/op          7 allocs/op
BenchmarkStructPartialSuccess-8                                  3000000               502 ns/op             256 B/op          6 allocs/op
BenchmarkStructPartialSuccessParallel-8                         10000000               225 ns/op             256 B/op          6 allocs/op
BenchmarkStructPartialFailure-8                                  2000000               702 ns/op             480 B/op         11 allocs/op
BenchmarkStructPartialFailureParallel-8                          5000000               329 ns/op             480 B/op         11 allocs/op
BenchmarkStructExceptSuccess-8                                   2000000               793 ns/op             496 B/op         12 allocs/op
BenchmarkStructExceptSuccessParallel-8                          10000000               193 ns/op             240 B/op          5 allocs/op
BenchmarkStructExceptFailure-8                                   2000000               639 ns/op             464 B/op         10 allocs/op
BenchmarkStructExceptFailureParallel-8                           5000000               300 ns/op             464 B/op         10 allocs/op
BenchmarkStructSimpleCrossFieldSuccess-8                         3000000               417 ns/op              72 B/op          3 allocs/op
BenchmarkStructSimpleCrossFieldSuccessParallel-8                10000000               163 ns/op              72 B/op          3 allocs/op
BenchmarkStructSimpleCrossFieldFailure-8                         2000000               645 ns/op             304 B/op          8 allocs/op
BenchmarkStructSimpleCrossFieldFailureParallel-8                 5000000               285 ns/op             304 B/op          8 allocs/op
BenchmarkStructSimpleCrossStructCrossFieldSuccess-8              3000000               588 ns/op              80 B/op          4 allocs/op
BenchmarkStructSimpleCrossStructCrossFieldSuccessParallel-8     10000000               221 ns/op              80 B/op          4 allocs/op
BenchmarkStructSimpleCrossStructCrossFieldFailure-8              2000000               868 ns/op             320 B/op          9 allocs/op
BenchmarkStructSimpleCrossStructCrossFieldFailureParallel-8      5000000               337 ns/op             320 B/op          9 allocs/op
BenchmarkStructSimpleSuccess-8                                   5000000               260 ns/op               0 B/op          0 allocs/op
BenchmarkStructSimpleSuccessParallel-8                          20000000                90.6 ns/op             0 B/op          0 allocs/op
BenchmarkStructSimpleFailure-8                                   2000000               619 ns/op             424 B/op          9 allocs/op
BenchmarkStructSimpleFailureParallel-8                           5000000               296 ns/op             424 B/op          9 allocs/op
BenchmarkStructComplexSuccess-8                                  1000000              1454 ns/op             128 B/op          8 allocs/op
BenchmarkStructComplexSuccessParallel-8                          3000000               579 ns/op             128 B/op          8 allocs/op
BenchmarkStructComplexFailure-8                                   300000              4140 ns/op            3041 B/op         53 allocs/op
BenchmarkStructComplexFailureParallel-8                          1000000              2127 ns/op            3041 B/op         53 allocs/op
BenchmarkOneof-8                                                10000000               140 ns/op               0 B/op          0 allocs/op
BenchmarkOneofParallel-8                                        20000000                70.1 ns/op             0 B/op          0 allocs/op
```

## Complementary Software

下面是一些使用了该库进行预验证或后验证的软件：

* [form](https://github.com/go-playground/form) - Decodes url.Values into Go value(s) and Encodes Go value(s) into url.Values. Dual Array and Full map support.
* [mold](https://github.com/go-playground/mold) - A general library to help modify or set data within data structures and other objects

## How to Contribute

Make a pull request...

## License
Distributed under MIT License, please see license file within the code for more details.

## Maintainers

This project has grown large enough that more than one person is required to properly support the community.
If you are interested in becoming a maintainer please reach out to me https://github.com/deankarn

## 原文链接

[https://pkg.go.dev/github.com/go-playground/validator/v10](https://pkg.go.dev/github.com/go-playground/validator/v10)