# Sarcio sidecar downloads

The [Sarcio](https://www.sarcio.io) sidecar runs beside your application so
approved server-side fixes take effect without a deploy. This repository holds
its downloads. The install and configuration guide is in the
[Sarcio docs](https://www.sarcio.io/docs#sidecar).

## Install

**Container** (Docker Compose, Kubernetes). Pin a version; there is no `latest`:

```
ghcr.io/sarcioai/sarcio-sidecar:0.2.2
```

**Linux or macOS host.** The install script picks the right file for the
machine (a deb or rpm package where the system uses them, otherwise the single
binary), checks it against the release's checksums and signature, and refuses
to install anything that does not match. Read it first, and pin a version in
production:

```bash
curl -fsSLO https://github.com/sarcioai/sarcio-sidecar-releases/releases/latest/download/install.sh
less install.sh
sh install.sh v0.2.2
```

**By hand.** Every file is on the
[Releases](https://github.com/sarcioai/sarcio-sidecar-releases/releases) page:
deb and rpm packages and plain binaries, for amd64 and arm64.

## Verify a download

Each release's `SHA256SUMS` is signed with
[minisign](https://jedisct1.github.io/minisign/):

```bash
minisign -Vm SHA256SUMS -P RWT/8gXBswXCZXMhfResaZIVGcwEjR/89MHEoYpo0C5ejHNUVTWiddoD
sha256sum --check --ignore-missing SHA256SUMS
```

The container image is signed with cosign; the public key and the command are
in the [docs](https://www.sarcio.io/docs#sidecar-verify).

## Support

[www.sarcio.io/docs](https://www.sarcio.io/docs), or email
[support@sarcio.io](mailto:support@sarcio.io).

## License

[Business Source License 1.1](LICENSE): production use to connect your own
applications to a Sarcio subscription or trial is granted; offering a competing
service is not. Each version converts to Apache-2.0 four years after its
release.
