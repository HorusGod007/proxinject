<img src="resources/proxinject.png" width="128" alt="logo">

# proxinject

*A proxy injection tool for **Windows**: just select some processes and make them proxy-able!*

> **Note**: This is a fork of [PragmaTwice/proxinject](https://github.com/PragmaTwice/proxinject) with additional features.

## New Features in This Fork

- **HTTP CONNECT Proxy Support**: In addition to SOCKS5, you can now use HTTP CONNECT proxies
- **Proxy Authentication**: Support for username/password authentication for both SOCKS5 and HTTP proxies
- New CLI options: `-t/--proxy-type`, `-U/--proxy-user`, `-W/--proxy-pass`

## Preview

### proxinject GUI

![screenshot](./docs/screenshot.png)

### proxinject CLI
```
$ ./proxinjector-cli -h
Usage: proxinjector-cli [options]

A proxy injection tool for Windows: just select some processes and make them proxy-able!

Optional arguments:
-h --help                       shows help message and exits
-v --version                    prints version information and exits
-i --pid                        pid of a process to inject proxy (integer)
-n --name                       short filename of a process with wildcard matching to inject proxy
-P --path                       full filename of a process with wildcard matching to inject proxy
-r --name-regexp                regular expression for short filename of a process to inject proxy
-R --path-regexp                regular expression for full filename of a process to inject proxy
-e --exec                       command line started with an executable to create a new process and inject proxy
-l --enable-log                 enable logging for network connections
-p --set-proxy                  set a proxy address for network connections (e.g. `127.0.0.1:1080`)
-t --proxy-type                 proxy type: socks5 (default) or http
-U --proxy-user                 proxy username for authentication
-W --proxy-pass                 proxy password for authentication
-w --new-console-window         create a new console window while a new console process is executed in `-e`
-s --subprocess                 inject subprocesses created by these already injected processes
```

### Examples

```sh
# Use SOCKS5 proxy (default)
proxinjector-cli -n chrome -p 127.0.0.1:1080

# Use HTTP CONNECT proxy
proxinjector-cli -n chrome -p 127.0.0.1:8080 -t http

# Use SOCKS5 proxy with authentication
proxinjector-cli -n chrome -p 127.0.0.1:1080 -U myuser -W mypass

# Use HTTP proxy with authentication
proxinjector-cli -n chrome -p 127.0.0.1:8080 -t http -U myuser -W mypass
```

## How to Install

Download the latest portable archive (`.zip`) or installer (`.exe`) from the [Releases Page](https://github.com/HorusGod007/proxinject/releases).

Or build from source:

```sh
git clone https://github.com/HorusGod007/proxinject.git
cd proxinject
./build.ps1 -mode Release -arch x64
# built binaries are in the `./release` directory
```

## Development Dependencies

### Environments:

- C++ compiler (with C++20 support, currently MSVC)
- Windows SDK (with winsock2 support)
- CMake 3

### Libraries:
(automatically fetched during build)

#### proxinjectee
- minhook
- asio (standalone)
- PragmaTwice/protopuf

#### proxinjector GUI
- asio (standalone)
- PragmaTwice/protopuf
- cycfi/elements

#### proxinjector CLI
- asio (standalone)
- PragmaTwice/protopuf
- p-ranav/argparse
- gabime/spdlog

## Credits

This project is forked from [PragmaTwice/proxinject](https://github.com/PragmaTwice/proxinject). All credit for the original implementation goes to the original author.

## License

Apache-2.0 License - See [LICENSE](LICENSE) for details.
