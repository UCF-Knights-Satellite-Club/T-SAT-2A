# T-SAT-2A

Tethered Satellite 2A: an ESP32 payload with dual Arducam Mega cameras, a BMP388 altimeter, a servo and an RFM95 LoRa link to a ground station.

## Layout

| Folder | Contents | Source |
|---|---|---|
| [`Software/`](Software/) | **Flight code** [`TSATA_FINAL.cpp`](Software/TSATA_FINAL.cpp) (cameras, altitude, servo, LoRa) and ground station [`TSATA_GND.cpp`](Software/TSATA_GND.cpp). Older variants are in `Archive/`. | ColdBloodV/KSC, May 2026 |
| [`Firmware/`](Firmware/) | PlatformIO project (`esp32dev`). `src/main.cpp` is the early camera skeleton; `test/` has the bring-up tests for the radio (LoRa TX/RX, ground station), cameras, servo, altimeter and ESP32. | SethJonesIntern/TSAT, Oct 2025 – Mar 2026 |
| [`Hardware/`](Hardware/) | KiCad projects for the **Connector PCB** and **Electronics PCB** (schematic, layout, PDFs, assembly drawings), the wiring diagram, and the symbol/footprint library the projects use | SethJonesIntern/TSAT, Feb 2026 |
| [`Hardware/Library (ColdBloodV May 2026)/`](<Hardware/Library (ColdBloodV May 2026)/>) | Later "fixed footprints" version of the same library | ColdBloodV/KSC, May 2026 |
| [`Docs/`](Docs/) | Flight software and ground station notes, system schematic image | ColdBloodV/KSC |
| [`BurnWire/`](BurnWire/) | Burn-wire release send/receive code and notes | ColdBloodV/KSC (`T-SAT/`) |

## Building the firmware

Open `Firmware/` in PlatformIO. The Arducam Mega library is fetched from [ArduCAM/Arducam_Mega](https://github.com/ArduCAM/Arducam_Mega) v3.0.0 through `lib_deps` instead of being copied into `lib/`. Set `upload_port`/`monitor_port` in `platformio.ini` for your machine.

## Open items

- **Footprint libraries disagree.** Six footprints (BMP388, camera connector, crimp, ESP32 DEV, RFM69HCW, servo) differ between `Hardware/Symbols & Footprints/` and the later `Hardware/Library (ColdBloodV May 2026)/`. Check which matches the boards that were built, keep that one, and delete the other.
- `Software/TSATA_FINAL.cpp` is plain C++ outside the PlatformIO project. Move it into `Firmware/src/` if the PlatformIO project becomes the build of record.

## History

Assembled from [ColdBloodV/KSC](https://github.com/ColdBloodV/KSC) (`TSAT2-A/`, `T-SAT/`) and [SethJonesIntern/TSAT](https://github.com/SethJonesIntern/TSAT) as a snapshot; see those repos for per-file history. Contributors: Seth Jones, alexsandersalazar, Yuliia, Francesca / France (ColdBloodV).
