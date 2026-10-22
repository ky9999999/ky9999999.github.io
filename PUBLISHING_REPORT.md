# GitHub Pages publication report

## 1. Broken internal links (target missing from repo)
- `index.html` -> `aki/index.html`; `index_j.html` -> `aki/index_j.html`
- `cv.html` -> `award/*` (6 files: certificates for JGR2025, GRL2025 (.pdf/.png), top-cited2025, RAS.GJI 2024, JGR2024 reviewer)
- `correction.html` and `data.html` -> `pub/JGR2022/{AMRFs,source-history,waveforms20210320,waveforms20210501}.jpg`
- `data.html` -> `pub/` data files (GJI2023, GL2019, EPSL2021, GJI2020, GRL2025, Tectono2015/2018, JGR2014/2018, EPSL2012) and directories `pub/Tecto2019/`, `pub/JGR2017/`, `pub/JGR2020/`, `pub/JGR2020b`.
  The entire `pub/` tree is absent from the repository.
- All `teleAMRFs/` links resolve.

## 2. Old-university-server dependencies
- `contents.html`, `main.html`: canonical URL and visible text point to `https://www.aob.gp.tohoku.ac.jp/~yoshida/`. Canonical changed to `https://ky9999999.github.io/`; visible text left unchanged (content). These are redirect stubs and could be replaced by `index.html`.
- `pub/`, `aki/`, `award/` were presumably served from that server and must be copied over.
- `http://nds-tohoku.in.arena.ne.jp/...58-5.pdf` (publication*.html) is an external journal site over plain HTTP, not the university server.

## 3. Files over 100 MB
No file in the repository exceeds 100 MB (largest: `profile.JPG`, 1.8 MB). The two named archives are **not referenced anywhere** in the HTML:
- `pub/EPSL2021/AMRFs_20230227.tar.gz`: no reference.
- `pub/GJI2023/repository20230306.tar.gz`: no reference. `data.html` previously linked the older `repository20230223.tar.gz`; now replaced by 20230306.
Their sizes cannot be verified here; if >100 MB, host them as release assets.

## 4. Release links (tag `archive-2026`)
- `data.html`: GJI2023 link changed from `./pub/GJI2023/repository20230223.tar.gz` to `https://github.com/ky9999999/ky9999999.github.io/releases/download/archive-2026/repository20230306.tar.gz` (description unchanged).
- EPSL2021: `https://github.com/ky9999999/ky9999999.github.io/releases/download/archive-2026/AMRFs_20230227.tar.gz`. The page has no existing link to this file, so the URL is kept in an HTML comment in `data.html` rather than inventing new visible content.

## 5. Re-check against latest `main` (merged into this branch)
Re-ran the link check over all `.html`/`.htm` files, now including `pub/`, `aki/`, `award/`.
- All links in the root pages, `teleAMRFs/`, `aki/index*.html`, `cv.html`, `data.html`, `correction.html` now resolve. No file is over 25 MB; no `_`-prefixed paths (Jekyll-safe); no mixed-content `http://` GitHub links.
- Fixed: `pub/{GRL2019,JGR2019,JGR2020,JGR2020b,Tecto2019}/index.html` "Home" link pointed to the old university server; now `https://ky9999999.github.io/`.
- Fixed: legacy `pub/Tectono2015/data.html` linked the old `repository20230223.tar.gz`; now the `archive-2026` 20230306 release asset.
- `data.html` GJI2023 link already points to the release. The EPSL2021 `AMRFs_20230227.tar.gz` URL is still only an HTML comment (no existing visible entry; no wording invented).

### Remaining issues (not changed)
- `pub/elast/index.html`: 15 PDFs (`1st.pdf` ... `botsu.pdf`, `9-2_20180722.pdf`, `11_20190722.pdf`) and `pub/style1.css` (referenced as `../style1.css`; only the root `style1.css` exists) do not exist.
- `pub/Tectono2015/data.html`: unlinked legacy copy of an old data page; its relative paths (`./pub/...`, `style1.css`) are wrong from that folder, so many links break. Nothing links to it; consider deleting or fixing.
- `aki/chosakuyori/*.htm`: `sono2...` links flagged by the checker are Shift_JIS/entity artifacts (e.g. fullwidth `ｎ` in filenames); verify in a browser.
- `Claude outputs/profile_crop_preview.jpg` is a stray folder name with a space; harmless but could be removed.
- `contents.html`/`main.html` visible text still mentions the old URL (content, left as is).
- Contact emails `@tohoku.ac.jp` are unchanged (addresses, not server dependencies).
