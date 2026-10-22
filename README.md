# sandbox-api-center

Source of truth for the API catalog shown by the Zudoku portal (`zudoku-sandbox`).
The portal clones this repo at `dev`/`build` time, so publishing a new API or version
here is enough — the portal repo needs no commit.

## Layout

```
apis.json                 # manifest: one entry per API, with its versions
apis/<api-id>/<version>.yaml   # OpenAPI specs
docs/                     # guides and conventions (see docs/CONTRIBUTING.md)
```

## Manifest (`apis.json`)

| Field | Required | Notes |
|-------|----------|-------|
| `id` | yes | Used in the URL: `/api-store/<id>` |
| `name`, `description` | yes | Shown on the API Store card |
| `status` | yes | `stable`, `beta` or `deprecated` |
| `category` | yes | Free text, shown on the card |
| `tags` | no | Searchable keywords |
| `versions[]` | yes | `{ id, label, file }`. One version → flat URL; several → version selector (`/api-store/<id>/<version>`) |

## Adding an API or a version

1. Add the spec under `apis/<api-id>/<version>.yaml`.
2. Add the API (or the new version) to `apis.json`.
3. Merge to `main`. The portal picks it up on its next `npm run dev` / `npm run build`.
