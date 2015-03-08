GoCodingConventions
===================

Go语言编码上的一些约定，自用。 v0.1.0.150308

### 版本号
每个包提供一个Version的常量，用于表示当前包的版本号，格式为：major.minor.patch.date。
类似于[semver](http://semver.org/lang/zh-CN/)，但相较于semver多了个date，用于表示最后修改的日期。


### import
- 禁止使用相对路径导入，所有库必须符合go get的需求。
- 将导入的包以空行分成以下几个部分：标准库，第三方包，仅用于初始化的包放最后。如：
```go
import(
    "os"
    "fmt"

    "golang.org/x/tools/godoc"
    "code.google.com/p/go.tools/cmd"

    _ github.com/mattn/go-sqlite3
)
```


### error
- 能用fmt.Errorf或是errors.New创建的，尽量不要自定义，保持error的简单；
- error提示信息中，应该以所在的函数开头，方便定位错误：
```go
    func triger () error {
        return errors.New("triger:出错了")
    }
```


### 命名规则

不要定义与保留函数相同名称的函数，但是作为一个结构方法时是允许的，比如:
```go
func print(...) { // 不行
    // todo
}

func (s *Struct) close () {
    // todo
}
```


### 文档

godoc会将文档中的换行符转换成一个空格，这样的排版在中文上是很难看的，
所以中文文档一律以标点作为一行的结束。


### 测试用例

