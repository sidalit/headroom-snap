# Headroom snap

[![headroom](https://snapcraft.io/headroom/badge.svg)](https://snapcraft.io/headroom)

Snap packaging for [Headroom](https://github.com/headroomlabs-ai/headroom), a local context-compression proxy and MCP server for AI applications.

Unofficial build, not affiliated with or endorsed by the Headroom project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/headroom"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install headroom
sudo snap connect headroom:removable-media   # optional: /media, /mnt
headroom proxy --port 8787
```

Point your client at `http://127.0.0.1:8787` for Anthropic or `http://127.0.0.1:8787/v1` for OpenAI-compatible requests, keeping its existing credentials. The dashboard is at http://127.0.0.1:8787/dashboard.

For MCP, configure your client to run `/snap/bin/headroom` with arguments `mcp serve`. Keep the proxy running. The cache-TTL helper is available as `headroom.cache-ttl`.

## Known limitations

- Host agent launching, `wrap`, `deploy` and automatic MCP registration are unavailable. Configure clients manually to use the proxy or MCP command.
- Files must be in a non-hidden home folder or connected removable storage. Hidden files directly under your home directory are inaccessible.
- Includes proxy, MCP, code compression and Bedrock support. Optional PyTorch, image/voice processing and extra SDK integrations are not included; models download on first use.
- State and model caches live under `~/snap/headroom/common`. Updates use snapd; `headroom update` is unsupported.

## Update to a new upstream release

Change `version` in `snap/snapcraft.yaml`, then rebuild.

## Automation

Builds, publishing, and dependency updates use [snap-automation](https://github.com/sidalit/snap-automation).

## License

The packaging is MIT-licensed (see `LICENSE`). Headroom is Apache-2.0-licensed; its dependencies carry their own licenses.
