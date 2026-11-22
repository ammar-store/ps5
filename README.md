# Ammar Store PS5 Host

**Live host:** https://ammar-store.github.io/ps5/

Ammar Store's customized fork of [SCORPION's PS5 host](https://github.com/scorpion511/PS5-SCORPION), using the Relapse exploit chain.

## Firmware support

The host accepts these exact firmware versions:

- 7.00, 7.01, 7.20, 7.40, 7.60, 7.61
- 8.00, 8.20, 8.40, 8.60
- 9.00, 9.20, 9.40, 9.60
- 10.00, 10.01, 10.20, 10.40, 10.60
- 11.00, 11.20, 11.60
- 12.00, 12.02, 12.20, 12.40, 12.60, 12.70
- 13.00, 13.20, 13.40, 13.42, 13.60

This is not a claim that every firmware between 7.00 and 13.60 works. Payloads may have their own compatibility requirements. The November 22, 2026 update does not change the firmware gate, offsets, WebKit/Relapse exploit chain, or the bundled etaHEN binary.

## Use

Open the live host in the console browser environment. Once the host reports that the ELF loader is ready:

- X selects or deselects a payload.
- D-pad up/down moves the cursor.
- L2 sends the selected payloads in menu order.
- R1 sends etaHEN only.

The host's ELF loader uses port 9021. Select only payloads appropriate for your setup. Do not assume that all HEN and mount tools should run together.

## Selectable payloads

| Tool | Bundled file |
| --- | --- |
| WebKit Autoloader v0.8.3 (latest) | `autoloader.elf` |
| Kstuff-lite v1.11 | `kstuff.elf` |
| Kraken Mount (run PKG games) | `kraken-mount.elf` |
| PS5 Dump Forge v0.5.6 (convert to FPKG) | `ps5-dump-forge-0.5.6-ps5.elf` |
| ShadowMountPlus 1.7 Beta 12 | `shadowmountplus.elf` |
| ELF loader v0.28 | `elfldr-ps5.elf` |
| Web File Manager v1.12 | `web-file-mgr-v1.12.elf` |
| NanoDNS PS5 | `nanodns.elf` |
| OnionHEN v0.9.0 | `OnionHEN.elf` |
| Prospero Menu v1.1.0 | `ProsperoMenu.elf` |
| LZ4 Game Compressor beta.7 | `LZ4-Game-Compressor.elf` |
| etaHEN, existing bundle | `etaHEN.elf` |
| PS5 App Dumper v2.10 | `ps5-app-dumper_v2.10.elf` |
| Game Compressor v1.1.5 (keieksof fork) | `game-compressor.elf` |
| Payload Manager v0.6.3 | `pldmgr_v0.6.3.elf` |
| WebKit Autoloader, firmware 5.00-11.60 entry | `autoloader.elf` |
| WebKit Autoloader, firmware 12.40-13.60 entry | `autoloader.elf` |

The menu list and its order match upstream SCORPION. The two firmware-ranged Autoloader entries and the latest entry all serve the current v0.8.3 build, which covers firmware 5.00-13.60.

### November 22, 2026 update

The menu now matches upstream SCORPION's full payload list, with every binary at its newest verified official release:

- [WebKit Autoloader v0.8.3](https://github.com/itsPLK/ps5-webkit-autoloader/releases/tag/v0.8.3) replaces v0.6.1 (upstream lists v0.8.1).
- [PS5 Dump Forge v0.5.6](https://github.com/quer3q/ps5-dump-forge/releases/tag/v0.5.6) replaces v0.4.0 (upstream bundles v0.5.5).
- [ShadowMountPlus 1.7 Beta 12](https://github.com/drakmor/ShadowMountPlus/releases/tag/1.7beta12) replaces Beta 7 (upstream bundles Beta 11).
- [elfldr v0.28](https://github.com/ps5-payload-dev/elfldr) replaces v0.27 (upstream bundles v0.27).
- Game Compressor upgraded to [keieksof's fork v1.1.5](https://github.com/keieksof/PS5-Game-Compressor), the newest active continuation; upstream bundles the older original.
- Kraken Mount, Web File Manager v1.12, and NanoDNS added from upstream SCORPION's bundle.
- Kstuff-lite v1.11, OnionHEN v0.9.0, Prospero Menu v1.1.0, LZ4 Game Compressor beta.7, PS5 App Dumper v2.10, and Payload Manager v0.6.3 were already at their latest official releases and are unchanged.
- etaHEN kept its existing bundled build. The newest official standalone release is [2.5B](https://github.com/etaHEN/etaHEN/releases), but this host's etaHEN comes from SCORPION's tested bundle and was not swapped.

ShadowMountPlus Beta 12 changes the configuration format to v2, migrates settings on first run, and requires restoring backups when downgrading. The project warns that image mounting can cause shutdown problems and internal-drive data corruption. Review its documentation and back up important data before using mount tools.

## Offline cache

The service worker caches the host page, Ammar Store images, JavaScript, firmware offsets, and active payload files. Allow the first online load to finish before going offline. Browser storage limits or clearing website data can remove cached files. After an update, reload online to install the new cache.

The November 22 maintenance update fixes the service-worker syntax, removes nonexistent cache paths, bumps the cache to version v6 with all current payload files, and makes the selected-payload send queue follow the actual menu entries instead of an outdated hard-coded list.

Checks cover source syntax, file references, binary hashes, and the deployed web page. They are not tests on a physical PS5 and do not guarantee exploit success or console stability.

## Credits and license

- Ammar Store: this fork's branding, background, and deployment.
- Ahmed Essam / SCORPION: upstream host.
- Original framework: muhammad10yaser.
- Exploit contributors credited by the host: ntfargo, ufm42, Sonic-Iso, Jordy, Dr. Yenyen, TheFlow, SlidyBat, Flatz, cow, nhk, bollarz, Sleirsgoevy, EchoStretch, EarthOnion.
- Payload authors retain their own credits and licenses. See the linked official projects and the repository's LICENSE.

Use only with systems and software you are authorized to test. Exploit execution and payloads can crash the console or affect stored data.
