# DJConnect Pi Releases

Public release distribution repository for the DJConnect Raspberry Pi touch
client.

This repository intentionally contains no application source code. It is used by
installed Raspberry Pi clients to download unattended app updates without
requiring a GitHub token on the device.

Source development happens in:

- `pcvantol/djconnect-pi`

## Release Assets

Each GitHub release should contain:

- `djconnect-pi-<version>.tar.gz`
- `djconnect-pi-<version>.sha256`

The Raspberry Pi updater downloads both files, verifies the SHA256 checksum and
installs the release atomically under:

```text
/opt/djconnect/releases/<version>
/opt/djconnect/current -> /opt/djconnect/releases/<version>
```

After installing a new release, the updater restarts:

- `djconnect-api.service`
- `djconnect-client.service`

## Update Channels

DJConnect Pi supports two update channels:

- `stable`: normal GitHub releases only
- `beta`: normal releases plus GitHub prereleases

The channel is configured on the Pi touch screen in Settings. The unattended
updater reads `/opt/djconnect/config/client.json`, including:

```json
{
  "update_repo": "pcvantol/djconnect-pi-releases",
  "update_channel": "stable"
}
```

## Publishing

Release assets are published from the private/source repository by GitHub
Actions. The source repository must have a secret named
`DJCONNECT_RELEASES_TOKEN` with permission to create releases in this repository.

Expected flow:

1. Tag the source repository with `vX.Y.Z`.
2. The source workflow runs tests.
3. It builds the release tarball and SHA256 file.
4. It creates a matching release in this public repository.

## Manual Verification

To inspect the latest releases:

```sh
gh release list --repo pcvantol/djconnect-pi-releases
```

To test an installed Pi updater without installing:

```sh
/opt/djconnect/current/bin/djconnect-pi-updater \
  --config /opt/djconnect/config/client.json \
  --install-root /opt/djconnect \
  --dry-run
```
