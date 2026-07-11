# DJConnect Pi Releases

DJConnect. Muziekbediening met karakter.

DJConnect lets you ask for music and get it personally announced through Home
Assistant. This public repository distributes release artifacts and public
metadata for the DJConnect Raspberry Pi touch client.

The Raspberry Pi client pairs with the DJConnect Home Assistant integration and
sends playback, queue, playlist and voice requests through Home Assistant.
Spotify credentials and Home Assistant long-lived tokens are not stored on the
Pi client.

## Repository Scope

This repository intentionally contains no application source code. It is used by
installed Raspberry Pi clients to download unattended app updates without
requiring a GitHub token on the device.

Source development happens in:

- `pcvantol/djconnect-pi`

## Requirements

- Home Assistant with the DJConnect integration installed and configured.
- Spotify Premium for playback control through Spotify.
- A configured Home Assistant Assist pipeline with working STT and TTS for
  voice/DJ announcements.
- Raspberry Pi client on the same local network as Home Assistant for pairing
  and local Client API callbacks.
- Working local networking/mDNS when using automatic discovery.

## Pairing

1. Open DJConnect on the Raspberry Pi client.
2. Let Home Assistant discover the client through mDNS, or copy the visible
   pairing details from the client:
   - Koppelcode / Pairing code
   - Client API URL
3. Open the DJConnect integration setup in Home Assistant.
4. Choose the Raspberry Pi client type and select or paste the pairing details.
5. Wait for the client to show that pairing completed.

The Pi client should advertise itself through Bonjour/mDNS as `_djconnect._tcp`
while its local Client API is active. Home Assistant may use discovery to find
the client, but the client still validates pairing through the visible pairing
code.

Pairing creates a DJConnect bearer token for this Pi installation. Discovery
alone never marks the client as paired.

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

## Privacy And Security

The Raspberry Pi client does not store Spotify credentials and does not store
Home Assistant long-lived access tokens. Device tokens are generated during
pairing and are scoped to DJConnect runtime calls. Diagnostics and logs should
never include bearer tokens, Spotify tokens, Home Assistant tokens or
passwords.

## Related Links

- Website: [https://djconnect.pages.dev](https://djconnect.pages.dev)
- Home Assistant integration: [pcvantol/djconnect](https://github.com/pcvantol/djconnect)
- ESP firmware releases: [pcvantol/djconnect-firmware](https://github.com/pcvantol/djconnect-firmware)
- Apple app releases: [pcvantol/djconnect-app-releases](https://github.com/pcvantol/djconnect-app-releases)

## Release Policy

This repository is intentionally small and contains public release metadata and
distributable Raspberry Pi client artifacts only. Old releases may be cleaned
up so that only the latest supported public release remains available.

## Legal

Copyright (c) 2026 Peter van Tol. All rights reserved.

Spotify is a trademark of Spotify AB. DJConnect is not affiliated with,
endorsed by, or sponsored by Spotify AB.
