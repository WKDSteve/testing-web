# testing-web

The page of testing-desktop as a single HTML file that Chrome opens
from disk (`file://`). It shows the test and CI results of the repositories that use testing.nvim. No install, no
server, no host: the file makes no network request (its CSP forbids it), and the results come from a local export
folder you pick in the browser.

This repository holds only the built page `testing.html`, its sums in `SHA256SUMS` and this README. The sources live
in testing-desktop; its build writes here. Do not edit these files by hand. There is no data in this repository: the
export folder is written by testing.nvim and kept in a separate place.

## Status

Not built yet. `testing.html` and `SHA256SUMS` appear here with the first release of testing-desktop.

## Use

```
git clone https://github.com/WKDSteve/testing-web.git
```

1. `git pull`, then check the file against `SHA256SUMS`:
   - Windows (PowerShell): `Get-FileHash testing.html` must match the line for `testing.html` in `SHA256SUMS`.
   - Linux, macOS, Git Bash: `sha256sum -c SHA256SUMS` must print `testing.html: OK`.
2. Open `file:///C:/repos/testing-web/testing.html` in Chrome (adjust the path) and bookmark it. That bookmark is the
   way to start the page; there is no start script.
3. Pick the export folder. After a restart of Chrome the page shows the folder used last: allow access once (no
   picker).
4. The page reads the folder again when the tab gets focus, or within 30 seconds. It never writes into it.

The page only reads. It does not start test runs, does not fetch CI results and needs no token: what it shows is as
old as the last export. Links to CI runs open GitHub in a new tab; that is a plain link, not a request of the page.

Every local HTML file in Chrome shares the origin `file://`, so open no other local page you do not trust in the same
profile.
