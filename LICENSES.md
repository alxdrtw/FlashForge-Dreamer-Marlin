# Licenses and redistribution checklist

This document is **not** a software license for Dreamer Studio. The application owner's chosen license and the licenses of its dependencies must be determined before source/binary publication.

## Firmware

- The customized firmware is described as based on Marlin 2.0.9.7 and https://github.com/moonglow/FlashForge_Marlin.
- The supplied project manual identifies the Marlin source bundle as GPL-3.0.
- If distributing a customized Marlin binary, include the complete corresponding source code (including modifications and build instructions), applicable copyright notices and the license text. Verify the exact obligations for the specific upstream code in use.

## Third-party components

Inspect firmware images, Cura definitions, bridge code, Python dependencies, icons and other assets for authorship and license requirements before publishing.

## Pre-publication checklist

- [ ] Check that no passwords, tokens, private keys or personal identifiers are embedded.
- [ ] Include the source code and full license terms required for the modified Marlin firmware.
- [ ] Choose an explicit license for original Dreamer Studio application code.
- [ ] Audit all third-party redistributable files and attribution requirements.
- [ ] Add the actual EXE under GitHub Releases and verify its SHA-256.
- [ ] Test download, first launch and firmware flashing on a supported test machine.
