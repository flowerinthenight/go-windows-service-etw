# Windows service in Go

This service is based on [this](https://godoc.org/golang.org/x/sys/windows/svc/example) example. The aim is to have a minimal ETW support for real-time logging which is helpful in debugging Windows services.

# ETW DLL

`disptrace.dll` is an x64 build of the `disptrace` project [here](https://github.com/flowerinthenight/win32-etw-manifest). This dll exports a single ETW function called ETWTrace. The service then imports this function dynamically.

# TODO

* Do not rely on external DLL.

# License

[The MIT License](./LICENSE.md)
