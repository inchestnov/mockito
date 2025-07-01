# Mockito — Go library for mocking interfaces

**Note: Next text is a concept, that not implemented yet.**

# Examples
Mock method:
```go
type DemoClient interface {
	Foo(arg string) string
}

var mock DemoClient = mockito.New[DemoClient]()
mockito.Return("value").
	When(mock).Foo("bar")

mock.Foo("bar") // value
```

Mock _void_ method:
```go
type Executor interface {
	Execute(ctx context.Context)
}

executor := mockito.New[Executor]()
mockito.DoNothing().
	When(executor).Execute(mockito.Any[context.Context]())

mockito.Do(func(ctx context.Context) { ... }).
	When(executor).Execute(mockito.Any[context.Context]())
```
