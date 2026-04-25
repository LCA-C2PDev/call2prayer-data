# Call2Prayer.PROPlus Data

Static prayer-data hosting for **Call2Prayer.PROPlus** via **GitHub Pages** on:

**Base site:** `https://data.call2prayer.net`  
**Data root:** `https://data.call2prayer.net/data/`

This repository publishes `.c2p` data files for client download over HTTPS.

---

## Purpose

This repository is the public data host for `Call2Prayer.PROPlus`. It is intended for small static Cal2Prayer PROPlus platform validation and geo-ops and almanac string data that can be fetched directly by the application.

Example public file URL:

```text
https://data.call2prayer.net/data/CLOUDLINX.AEDXB_CITY.c2p
```

---

## File Naming Standard

Published data files use this naming format:

```text
CLOUDLINX.<UNLOCODE>_<AreaName>.c2p
```

### Rules

- `CLOUDLINX` is the fixed prefix.
- `<UNLOCODE>` is the location code.
- `<AreaName>` is the area name.
- If the area name is not available, use `CITY`.

### Example

```text
CLOUDLINX.AEDXB_CITY.c2p
```

---

## Repository Structure

```text
/
├── data/
│   ├── CLOUDLINX.AEDXB_CITY.c2p
│   └── ...
├── manifest.json
├── index.html
├── CNAME
└── README.md
```

---

## Published Endpoints

### Site root

```text
https://data.call2prayer.net/
```

### Manifest

```text
https://data.call2prayer.net/manifest.json
```

### Example data file

```text
https://data.call2prayer.net/data/CLOUDLINX.AEDXB_CITY.c2p
```

---

## `manifest.json`

The `manifest.json` file is the public index used by clients to discover available `.c2p` files.

Example:

```json
{
  "name": "Call2Prayer.PROPlus Data",
  "baseUrl": "https://data.call2prayer.net/data/",
  "files": [
    "CLOUDLINX.AEDXB_CITY.c2p"
  ]
}
```

### Requirements

- `baseUrl` must remain:

```text
https://data.call2prayer.net/data/
```

- Each published `.c2p` file should be listed in the `files` array.
- A filename should appear only once.

---

## Add a New `.c2p` File

1. Upload the new file into the `data/` folder.
2. Keep the filename in the correct format.
3. Add the filename to the `files` array in `manifest.json`.
4. Commit the changes to the `main` branch.
5. Verify both the manifest and the direct file URL.

Example target format:

```text
https://data.call2prayer.net/data/<filename>
```

---

## Update an Existing `.c2p` File

If the filename stays the same:

1. Replace the file in `data/` with the updated version.
2. Commit the change to `main`.
3. Do **not** change `manifest.json` if the filename is unchanged.
4. Verify the public file URL again.

---

## Delete a `.c2p` File

1. Delete the file from `data/`.
2. Remove the same filename from `manifest.json`.
3. Commit both changes to `main`.
4. Verify that the file is no longer publicly accessible.

---

## Verification Checklist

After any add, update, or delete, verify:

### Manifest

```text
https://data.call2prayer.net/manifest.json
```

Check that:
- the file list is correct
- deleted files are removed
- newly added files are present

### Direct file access

Example:

```text
https://data.call2prayer.net/data/CLOUDLINX.AEDXB_CITY.c2p
```

Check that:
- the file is reachable when expected
- replaced files serve updated content
- deleted files are no longer available

---

## Publishing Workflow

This repository is published through **GitHub Pages** from the `main` branch.

Typical maintenance flow:

1. Upload, replace, or delete file(s) in `data/`
2. Update `manifest.json` if filenames changed
3. Commit to `main`
4. Wait for GitHub Pages to republish
5. Verify public access on `data.call2prayer.net`

---

## Hosting Details

- **Domain:** `call2prayer.net`
- **Custom data host:** `data.call2prayer.net`
- **Hosting platform:** GitHub Pages
- **DNS provider:** Marcaria

---

## Notes for Maintainers

- Keep filenames exact.
- Do not upload `.c2p` files outside the `data/` folder.
- Do not forget to update `manifest.json` when adding or deleting files.
- Use HTTPS URLs when testing public access.
- If a replaced file appears stale in the browser, force refresh or test in a private window.
