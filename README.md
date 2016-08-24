# Windows service in Go

This service is based on [this](https://godoc.org/golang.org/x/sys/windows/svc/example) example.

# ETW DLL

`disptrace.dll` is an x64 build of the `disptrace` project [here](https://github.com/flowerinthenight/win32-etw-manifest). This dll exports a single ETW function called ETWTrace. The service then imports this function dynamically.

# Licence

[The MIT License](./LICENSE.md)
