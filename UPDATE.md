# Updating Mi 11 Ultra Flash Tool

This repository's `main` branch is the source of truth for application updates.

## Automatic update

When the tool is packaged for end users, its updater may check **only the `main` branch** for application updates. It must never update from feature branches, development branches, pull requests, or an arbitrary GitHub Release.

An automatic update must:

1. Refuse to run while a device operation is active.
2. Download application content into a temporary staging area.
3. Validate the staged application before replacement.
4. Keep the current known-good version until the replacement succeeds.
5. Restore the previous version if startup or validation fails.

## Manual update

For source checkouts:

```powershell
git fetch origin main
git merge --ff-only origin/main
```

If the project later gains NuGet or other dependencies, restore them from the declared project manifests after updating:

```powershell
dotnet restore
```

Use `git merge --ff-only` so an update never silently overwrites local changes or merges unrelated history.

## Dependency policy

Do not add packages that are deprecated or unmaintained when a supported replacement exists. Dependency changes must be restored and built or tested before being used for a release.

## Release policy

The project uses semantic versioning:

- **PATCH** — bug fixes and documentation-only release fixes.
- **MINOR** — backward-compatible features and safety improvements.
- **MAJOR** — incompatible workflow or configuration changes.

Git tags and GitHub Releases may still provide reproducible **manual** distribution and rollback points, but they are not an automatic-update source.

## Safety note

Do not auto-update firmware, ROM images, boot images, or device partitions. Only the application itself may be updated automatically. Firmware and flashing inputs always require explicit operator selection and confirmation.
