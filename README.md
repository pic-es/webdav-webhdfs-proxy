# ASGI WebDAV Server

This repository is a fork of [ASGI-WebDAV](https://github.com/rexzhang/asgi-webdav).
The main added feature is a proxy that allows WebDAV over WebHDFS.
These changes are being considered for inclusion in the main repository.

[![GitHub](https://img.shields.io/github/license/pic-es/webdav-webhdfs-proxy)](https://github.com/pic-es/webdav-webhdfs-proxy/blob/main/LICENSE)
[![PyPI](https://img.shields.io/pypi/v/ASGIWebDAV)](https://pypi.org/project/ASGIWebDAV)
[![PyPI - Version](https://img.shields.io/pypi/pyversions/ASGIWebDAV.svg)](https://pypi.org/project/ASGIWebDAV/)
![Pytest Workflow Status](https://github.com/pic-es/webdav-webhdfs-proxy/actions/workflows/check-pytest.yml/badge.svg)
[![codecov](https://codecov.io/gh/pic-es/webdav-webhdfs-proxy/branch/main/graph/badge.svg?token=6D961MCCWN)](https://codecov.io/gh/pic-es/webdav-webhdfs-proxy)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Docker Pulls](https://img.shields.io/docker/pulls/ray1ex/asgi-webdav)](https://hub.docker.com/r/ray1ex/asgi-webdav)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/ASGIWebDAV)](https://pypi.org/project/ASGIWebDAV)
[![GitHub Downloads](https://img.shields.io/github/downloads/pic-es/webdav-webhdfs-proxy/total)](https://github.com/pic-es/webdav-webhdfs-proxy/releases)

An asynchronous WebDAV server implementation, Support multi-provider, multi-account and permission control.

## Features

- [ASGI](https://asgi.readthedocs.io) standard
- WebDAV standard: [RFC4918](https://www.ietf.org/rfc/rfc4918.txt)
- Support multi-provider: FileSystemProvider, MemoryProvider, WebHDFSProvider
- Support multi-account and permission control
- Support optional anonymous user
- Support optional home directory
- Support store password in raw/hashlib/LDAP(experimental) mode
- Full asyncio file IO
- Passed all [litmus(0.13)](http://www.webdav.org/neon/litmus) test, except 3 warning
- Browse the file directory in the browser
- Support HTTP Basic/Digest authentication
- Support response in Gzip/Brotli
- Compatible with macOS finder and Window10 Explorer

## Quickstart

[中文手册](https://pic-es.github.io/webdav-webhdfs-proxy/zh/)

```shell
docker pull ray1ex/asgi-webdav
docker run -dit --restart unless-stopped \
  -p 8000:8000 \
  -e UID=1000 -e GID=1000 \
  -v /your/data:/data \
  --name asgi-webdav ray1ex/asgi-webdav
```

## Default Account

|            | value      | description                     |
| ---------- | ---------- | ------------------------------- |
| username   | `username` | -                               |
| password   | `password` | -                               |
| permission | `["+"]`    | Allow access to all directories |

## View in Browser

![View in Browser](docs/web-dir-browser-screenshot.png)

## Documentation

[Documentation at GitHub Page](https://pic-es.github.io/webdav-webhdfs-proxy/)

## TODO

- Digest auth support neon
- SQL database provider
- Test big(1GB+) file in MemoryProvider
- display server info in page `/_/admin` or `/_/`
- Fail2ban(docker)
- NFSProvider
- logout at the web page
- Fix MemoryProvider with macOS finder(create new file)
- rewrite MemoryProvider with mmap
- generate template URL for share(read only)

## Related Projects

- <https://github.com/bootrino/reactoxide>
