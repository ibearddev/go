Высокопроизводительная замена "encoding/json", на 100% совместимая 

Вы также можете использовать бережный JSON, с помощью [thrift-iterator] (https://github.com/thrift-iterator/go)

# Benchmark

![benchmark](http://jsoniter.com/benchmarks/go-benchmark.png)

Исходники: https://github.com/json-iterator/go-benchmark/blob/master/src/github.com/json-iterator/go-benchmark/benchmark_medium_payload_test.go

Необработанный результат (easyjson требует генерации статического кода)

|                 | ns/op       | allocation bytes | allocation times |
| --------------- | ----------- | ---------------- | ---------------- |
| std decode      | 35510 ns/op | 1960 B/op        | 99 allocs/op     |
| easyjson decode | 8499 ns/op  | 160 B/op         | 4 allocs/op      |
| jsoniter decode | 5623 ns/op  | 160 B/op         | 3 allocs/op      |
| std encode      | 2213 ns/op  | 712 B/op         | 5 allocs/op      |
| easyjson encode | 883 ns/op   | 576 B/op         | 3 allocs/op      |
| jsoniter encode | 837 ns/op   | 384 B/op         | 4 allocs/op      |

Всегда ориентируйтесь на свою рабочую нагрузку.
Результат сильно зависит от ввода данных.

# Как использовать?

100% совместимость со стандартной библиотекой

Заменить

```go
import "encoding/json"
json.Marshal(&data)
```

на

```go
import jsoniter "github.com/json-iterator/go"

var json = jsoniter.ConfigCompatibleWithStandardLibrary
json.Marshal(&data)
```

Заменить

```go
import "encoding/json"
json.Unmarshal(input, &data)
```

на

```go
import jsoniter "github.com/json-iterator/go"

var json = jsoniter.ConfigCompatibleWithStandardLibrary
json.Unmarshal(input, &data)
```

[Больше в документации](http://jsoniter.com/migrate-from-go-std.html)

# Выполнить get

```
go get github.com/json-iterator/go
```
