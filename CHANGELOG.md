# Changelog

All notable changes to this project are documented here.

The project follows [Semantic Versioning](https://semver.org/).

## [0.1.1] - 2026-08-20

### Fixed
- Corrected process output/error redirection so command results can be read reliably.

### Safety
- Disabled the unsafe prototype path that attempted to unlock the bootloader automatically.
- Disabled direct flashing of a recovery ROM ZIP as the `system` partition.
- Added an explicit confirmation before flashing a selected `boot.img`.

## [0.1.0]

### Added
- Initial Windows Forms prototype and documented update foundation.
