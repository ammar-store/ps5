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

This is not a claim that every firmware between 7.00 and 13.60 works. Payloads may have their own compatibility requirements. The November 22, 2026 maintenance update does not change the firmware gate, offsets, WebKit/Relapse exploit chain, or etaHEN binary.

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
| WebKit Autoloader v0.6.1 | `webkit-autoloader-installer_v0.6.1.elf` |
| Kstuff-lite, existing bundle | `kstuff.elf` |
| ShadowMountPlus 1.7 Beta 7 | `shadowmountplus.elf` |
| OnionHEN | `OnionHEN.elf` |
| Prospero Menu | `ProsperoMenu.elf` |
| LZ4 Game Compressor | `LZ4-Game-Compressor.elf` |
| PS5 Dump Forge v0.4.0 | `PS5-dump-forge-0.4.0-ps5.elf` |
| ELF loader, existing bundle | `elfldr-ps5.elf` |
| etaHEN, existing bundle | `etaHEN.elf` |
| PS5 App Dumper v2.10 | `ps5-app-dumper_v2.10.elf` |
| Game Compressor | `game-compressor.elf` |
| Payload Manager v0.6.3 | `pldmgr_v0.6.3.elf` |
| Auto Loader, existing bundle | `autoloader.elf` |

Older payload files remain in the repository for compatibility/history, but the menu uses the files above.

### Binary maintenance status

The November 22 maintenance update fixes host-side cache and menu bugs only. The bundled binary versions listed above remain unchanged. Verified replacement releases have not yet been committed:

- [WebKit Autoloader v0.8.3](https://github.com/itsPLK/ps5-webkit-autoloader/releases/tag/v0.8.3)
- [PS5 Dump Forge v0.5.6](https://github.com/quer3q/ps5-dump-forge/releases/tag/v0.5.6)
- [ShadowMountPlus 1.7 Beta 11](https://github.com/drakmor/ShadowMountPlus/releases/tag/1.7beta11), matching SCORPION's bundle at the time of review.

ShadowMountPlus Beta 12 changes the configuration format to v2, migrates settings on first run, and requires restoring backups when downgrading. The project warns that image mounting can cause shutdown problems and internal-drive data corruption. Review its documentation and back up important data before using mount tools.

## Offline cache

The service worker caches the host page, Ammar Store images, JavaScript, firmware offsets, and active payload files. Allow the first online load to finish before going offline. Browser storage limits or clearing website data can remove cached files. After an update, reload online to install the new cache.

The November 22 maintenance update fixes the service-worker syntax, removes nonexistent cache paths, gives the cache a new version, and makes the selected-payload send queue follow the actual menu entries instead of an outdated hard-coded list.

Checks cover source syntax, file references, binary hashes, and the deployed web page. They are not tests on a physical PS5 and do not guarantee exploit success or console stability.

## Credits and license

- Ammar Store: this fork's branding, background, and deployment.
- Ahmed Essam / SCORPION: upstream host.
- Original framework: muhammad10yaser.
- Exploit contributors credited by the host: ntfargo, ufm42, Sonic-Iso, Jordy, Dr. Yenyen, TheFlow, SlidyBat, Flatz, cow, nhk, bollarz, Sleirsgoevy, EchoStretch, EarthOnion.
- Payload authors retain their own credits and licenses. See the linked official projects and the repository's LICENSE.

Use only with systems and software you are authorized to test. Exploit execution and payloads can crash the console or affect stored data.
