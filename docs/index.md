# ASGI WebDAV Server

This repository is a fork of [ASGI-WebDAV](https://github.com/rexzhang/asgi-webdav).
The main added feature is a proxy that allows WebDAV over WebHDFS.
These changes are being considered for inclusion in the main repository.

Welcome to the official documentation of the **WebDAV over WebHDFS Proxy** project.

This documentation covers the main topics to get started and dive deeper into the project.

---

## 📄 Main Documents

- [Changelog](changelog.en.md)
- [Compatibility](compatibility.en.md)
- [Contributing](contributing.en.md)
- [Install Guide](install.en.md)
- [Quick Start with Docker](quick-start-in-docker.en.md)
- [Known Issues](known-issues.en.md)
- [Troubleshooting](trouble-shooting.en.md)
- [How-to Guides](howto/)
- [User Guide](guide/)
- [Reference](reference/)

---

## Screenshot

![Web Directory Browser](web-dir-browser-screenshot.png)

---

_Last updated: {{ date }}_


# Overview

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

## Quick Start

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

![](web-dir-browser-screenshot.png)
