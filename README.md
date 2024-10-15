# errx

`errx` is a more modern and convenient error handling library, providing more user-friendly stacktrace:


# Install

```shell
go get github.com/reedchan7/errx
```


# Quick Start

```go
err := errx.New("oops: something wrong :(")
err = errx.Wrap(err, "failed to do something")
fmt.Printf("%+v\n", err)
```

# Example

```go
err := errx.NewInternalServerError().New("failed to do something")
err = errx.Wrap(err, "oops: :(")
err = errx.Wrapf(err, "xxxxxxx")
fmt.Printf("%+v\n", err)
```

Result:
```text
500: Internal Server Error: xxxxxxx: oops: :(: failed to do something
  Thrown: failed to do something
    --- at /home/user/go/pkg/errx/errx_test.go:17 TestCode1()
  Thrown: oops: :(
    --- at /home/user/go/pkg/errx/errx_test.go:18 TestCode1()
  Thrown: xxxxxxx
    --- at /home/user/go/pkg/errx/errx_test.go:19 TestCode1()
```
