# Updating Mi 11 Ultra Flash Tool

This repository is the source of truth for the project.

## Automatic update

When the tool is packaged for end users, the planned updater checks the project's GitHub Releases channel and offers a signed release update before flashing operations begin. Updates must never be applied while a device operation is running.

## Manual update

For source checkouts:

```powershell
git fetch origin main
git merge --ff-only origin/main
```

If the project later gains NuGet or other dependencies, restore them after updating:

```powershell
dotnet restore
```

Use `git merge --ff-only` so an updater does not silently overwrite local changes.

## Release policy

The project uses semantic versioning:

- **PATCH** — bug fixes and documentation-only release fixes.
- **MINOR** — backward-compatible features and safety improvements.
- **MAJOR** — incompatible workflow or configuration changes.

Every meaningful release should have a Git tag, GitHub Release notes, and a documented manual upgrade path.

## Safety note

Do not auto-update firmware, ROM images, boot images, or device partitions. Only the application itself may be updated automatically. Firmware and flashing inputs always require explicit operator selection and confirmation.
