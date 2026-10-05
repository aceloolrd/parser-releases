# Parser Releases

Public delivery channel for the Training Stand Parser.

This repository intentionally contains only public release metadata and declarative selector
configuration. Application source code, proxy data, credentials, browser profiles and user data
must never be published here.

## selectors.json

`selectors.json` is the lightweight selector channel used by the desktop application.

Rules:

- declarative JSON only;
- increment `config_version` for every published selector change;
- keep `schema_version` compatible with the installed application;
- publish only a complete validated configuration;
- never put tokens, cookies, proxy credentials or executable code in this repository.

Current initial remote publication uses the same selector content as the bundled configuration,
with a higher `config_version`, so the real remote-delivery path can be acceptance-tested safely.


## Application releases

Application binaries are attached to GitHub Releases, not committed to the repository.

For a production release `vX.Y.Z`, upload:

- `TrainingStandParser-X.Y.Z-win64.zip` — mandatory full fallback package;
- `TrainingStandParser-A.B.C-to-X.Y.Z-patch.zip` — optional incremental patches;
- `TrainingStandParser-X.Y.Z-Setup.exe` — optional installer for first installation/reinstall.

After a non-prerelease GitHub Release is published, the repository workflow validates the asset
names and patch sizes, computes SHA-256 hashes, refuses channel downgrade, and commits
`latest.json` automatically. Do not hand-edit `latest.json`.

This ordering ensures clients never see a manifest that points at assets which have not yet been
published.
