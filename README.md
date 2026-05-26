# HP S01-2020 Hackintosh EFI

OpenCore EFI for HP S01-2020 desktop.

## Hardware

- Model: HP S01-2020 desktop
- CPU: Intel Core i7-10700
- iGPU: Intel UHD Graphics 630
- Memory: 16 GB
- Storage: 256 GB SSD
- macOS: Sonoma 14.8.5
- SMBIOS: iMac20,1

## Status

- Boots macOS Sonoma
- UHD630 graphics works
- Audio layout: `alcid=11`
- USB mapped with `USBToolBox.kext` + `UTBMap.kext`
- OpenCore picker uses `Builtin`, no OpenCanopy GUI
- Debug boot arguments removed

## Important

Before using this EFI, generate your own SMBIOS values and replace these fields in `EFI/OC/config.plist`:

- `PlatformInfo -> Generic -> SystemSerialNumber`
- `PlatformInfo -> Generic -> MLB`
- `PlatformInfo -> Generic -> SystemUUID`
- `PlatformInfo -> Generic -> ROM`

Do not use the placeholder values as-is.

## Notes

This EFI is shared as a reference for the HP S01-2020 / Comet Lake / UHD630 platform. Review BIOS settings, USB mapping, network card, storage, and SMBIOS before using it on another machine.
