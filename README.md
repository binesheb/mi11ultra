# Mi 11 Ultra Flash Tool

A small Windows utility for working with Xiaomi Mi 11 Ultra devices using ADB and Fastboot.

## Goal

Make common Mi 11 Ultra recovery and developer workflows easier without requiring users to manually type every ADB/Fastboot command.

## Current state

The repository contains an early Windows Forms prototype. The next implementation steps are focused on **device detection, explicit confirmations, command logging, cancellation, and safer operation sequencing** before adding more flashing features.

## Important safety boundary

The current prototype should **not** be treated as a production-safe ROM flasher. In particular, a recovery ROM ZIP cannot generally be passed directly to `fastboot flash system`; device, firmware package type, partition layout, and bootloader state must be validated before any destructive command is run.

Future changes should therefore prefer validated, explicit operations over a one-click flashing sequence.

## Updates

The project has both a planned application update channel and a documented manual source update path. See [UPDATE.md](UPDATE.md).

## Versioning

Current source version: **0.1.0**. The project follows semantic versioning for future releases.

## Safety

Flashing firmware can erase data or make a device unbootable. Always verify the exact device, firmware package, required unlock state, and compatibility before running any flashing operation.

Never automatically download, select, or flash firmware without explicit operator confirmation.
