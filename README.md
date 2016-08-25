# Windows service in Go with ETW support

This service is based on [this](https://godoc.org/golang.org/x/sys/windows/svc/example) example. The aim is to have a minimal ETW support for real-time logging which is helpful in debugging Windows services.

# ETW DLL

`disptrace.dll` is an x64 build of the `disptrace` project [here](https://github.com/flowerinthenight/win32-etw-manifest). This dll exports a single ETW function called ETWTrace. The service then imports this function dynamically.

# Quickstart guide

#### Install the manifest file

```
admin prompt> wevtutil im jytrace.man /mf:"full-path-to-disptrace.dll" /rf:"full-path-to-disptrace.dll"
```

#### Use mftrace to capture real-time logs

The `mftrace.exe` tool is shipped together with Windows SDK/WDK and is located in `%ProgramFiles(x86)%\Windows Kits\<version>\bin\<arch>\`. You also need `mfdetours.dll` library.

```
admin prompt> mftrace.exe -c config.xml
```

### Build and run the service

```
go build
go-windows-service-etw.exe install
go-windows-service-etw.exe start (you should be able to see real-time logs here)
go-windows-service-etw.exe stop
go-windows-service-etw.exe remove
```

# TODO

- [ ] Do not rely on external DLL.

# License

[The MIT License](./LICENSE.md)
