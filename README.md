<div align="center">

<img src="snap/gui/headroom.png" alt="Headroom logo" width="128" />

# Headroom

**Compress AI context through a local proxy and MCP server.**

[![headroom](https://snapcraft.io/headroom/badge.svg)](https://snapcraft.io/headroom)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Headroom](https://github.com/headroomlabs-ai/headroom), a context-compression proxy for AI applications.

</div>

---

## Getting Started

<a href="https://snapcraft.io/headroom"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install headroom
headroom proxy --port 8787
```

Keep the proxy running. Point your client at `http://127.0.0.1:8787` for Anthropic, or `http://127.0.0.1:8787/v1` for OpenAI-compatible requests, using its existing credentials. The dashboard is at <http://127.0.0.1:8787/dashboard>.

## Configure

This snap has no `snap set` options. Use Headroom's command-line options; `headroom proxy --help` lists proxy settings.

For MCP, configure your client with command `/snap/bin/headroom` and arguments `["mcp", "serve"]`. The cache-TTL helper is available as `headroom.cache-ttl`.

```bash
sudo snap connect headroom:removable-media   # optional: /media, /mnt
```

State and downloaded model caches live under `~/snap/headroom/common`.

## Limitations

- Host agent launching, `wrap`, `deploy` and automatic MCP registration are unavailable. Configure clients manually.
- Files must be in a non-hidden home folder or connected removable storage; hidden files directly under your home are inaccessible.
- Includes proxy, MCP, code compression and Bedrock support. Optional PyTorch, image/voice processing and extra SDK integrations are not included.
- Models download on first use. Update with `sudo snap refresh headroom`; `headroom update` cannot replace the snap.

## Build

```bash
git clone https://github.com/sidalit/headroom-snap.git
cd headroom-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/headroom-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/headroomlabs-ai/headroom/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/headroom-snap/blob/main/LICENSE).
