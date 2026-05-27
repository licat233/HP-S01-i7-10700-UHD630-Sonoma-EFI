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
- HDMI/display wake after display sleep works with `igfxonln=1`
- USB mapped with legacy `USBMap.kext`; all tested ports work at USB2 speed
- CSR8510 A10 USB Bluetooth works with `BlueToolFixup.kext`
- OpenCore picker uses `Builtin`, no OpenCanopy GUI
- Debug boot arguments removed
- Current boot args: `alcid=11 darkwake=0 igfxonln=1`

## Power Notes

For daily use on this desktop, system sleep is intentionally disabled and display sleep can be used instead. The tested macOS power baseline is:

```bash
sudo pmset -a sleep 0 disksleep 0 hibernatemode 0 standby 0 powernap 0 proximitywake 0 ttyskeepawake 0
```

If display wake is unstable on your monitor or HDMI port, keep `igfxonln=1` in `boot-args`.

## Bluetooth Notes

External CSR8510 A10 USB Bluetooth is verified working on Sonoma with `BlueToolFixup.kext`.

## USB Notes

The current stable EFI keeps `SSDT-USB-Reset.aml` enabled and uses legacy `USBMap.kext`. On the tested HP S01 unit, all tested ports work reliably at USB2 speed under macOS. Front USB3 SuperSpeed behavior is not considered solved in this EFI.

## Important

Before using this EFI, generate your own SMBIOS values and replace these fields in `EFI/OC/config.plist`:

- `PlatformInfo -> Generic -> SystemSerialNumber`
- `PlatformInfo -> Generic -> MLB`
- `PlatformInfo -> Generic -> SystemUUID`
- `PlatformInfo -> Generic -> ROM`

Do not use the placeholder values as-is.

## Notes

This EFI is shared as a reference for the HP S01-2020 / Comet Lake / UHD630 platform. Review BIOS settings, USB mapping, network card, storage, and SMBIOS before using it on another machine.
