# edgelight-weather-ota

OTA update channel for the Edgelight weather display (ESP32).

## How it works

Devices poll `manifest.json` hourly. When the `version` field is newer than the running firmware, the device fetches the binary at the `url` field, verifies the `sha256`, and applies the update.

## Release procedure

1. Upload the new `.bin` file to this repo first.
2. Update `manifest.json` last — changing the manifest is what triggers devices to update.

Do not delete old binaries until a rollout is confirmed complete. Devices that missed the initial window may still be downloading the previous version.

## Important

The GitHub Pages URL for this repo (`https://adam-rho.github.io/edgelight-weather-ota/`) is burned into shipped firmware. **Never rename this repo without a migration plan** — renaming will break OTA for all devices in the field that have not yet received a firmware update pointing to the new URL.
