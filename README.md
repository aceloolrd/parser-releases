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
