# WSO2 Agent Builder

Open source AI agent building platform offering a powerful low-code development experience with enhanced capabilities.

## Releases

This repository hosts the **releases** of WSO2 Agent Builder. The source code lives in
[wso2/product-integrator](https://github.com/wso2/product-integrator), which builds both
WSO2 Integrator and WSO2 Agent Builder from one shared codebase; each release here names
the exact source commit it was built from in its release notes.

Agent Builder has its own version line, independent of WSO2 Integrator's.

### Downloads

Each release ships the following installers (plus `.pem`/`.sig`/`.sha256` sidecars):

| Platform | Artifact |
|---|---|
| Windows (x64) | `wso2-agent-builder-<version>.msi` |
| macOS (Apple silicon) | `wso2-agent-builder-<version>-arm64.dmg` |
| macOS (Intel) | `wso2-agent-builder-<version>-x64.dmg` |
| Linux (deb) | `wso2-agent-builder_<version>_amd64.deb` |
| Linux (rpm) | `wso2-agent-builder-<version>.x86_64.rpm` |
| Linux (tar) | `wso2-agent-builder-<version>-linux-x64.tar.gz` |

WSO2 Agent Builder installs side by side with WSO2 Integrator on every platform.

### Verifying a download

Artifacts are signed with [cosign](https://docs.sigstore.dev/) (keyless) **by the source
repository's release workflow**, so the certificate identity names
`wso2/product-integrator` — not this repository. That is expected: the builds are produced
there and only published here.

```bash
cosign verify-blob wso2-agent-builder-<version>.msi \
  --certificate wso2-agent-builder-<version>.msi.pem \
  --signature wso2-agent-builder-<version>.msi.sig \
  --certificate-identity-regexp 'https://github.com/wso2/product-integrator/\.github/workflows/.*' \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com
```

A SHA-256 checksum for each artifact is in its `.sha256` sidecar (OpenSSL `dgst` format);
compare it against your own digest:

```bash
openssl dgst -sha256 wso2-agent-builder-<version>.msi
cat wso2-agent-builder-<version>.msi.sha256
```

## Issues

Please report Agent Builder issues in this repository's
[issue tracker](https://github.com/wso2/product-agent-builder/issues). Code changes happen
in [wso2/product-integrator](https://github.com/wso2/product-integrator).

## License

See [LICENSE](LICENSE).
