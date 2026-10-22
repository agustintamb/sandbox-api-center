# Contributing

## Conventions

- One folder per API under `apis/`, one file per major version (`v1.yaml`, `v2.yaml`).
- `info.version` in the spec should match the `label` in `apis.json`.
- Keep `id` stable: it is part of public URLs. Add a new version instead of replacing one.
- Mark retired APIs with `"status": "deprecated"` rather than deleting them.

## Validation

Every file referenced by `apis.json` must exist. The portal's sync step fails the build
if a manifest entry points to a missing file.
