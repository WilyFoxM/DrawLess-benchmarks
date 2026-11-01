# DrawLess benchmark data

Raw measurements behind the published [DrawLess](https://github.com/WilyFoxM/DrawLess) benchmarks. The reports themselves, with every phase, the method, limitations and figures, are in the [benchmark report](https://github.com/WilyFoxM/DrawLess/blob/main/benchmarks/README.md); this repository only holds the original files they are computed from, so the main repository stays focused on the mod.

| Folder | Benchmark | Build | Recorded |
|---|---|---|---|
| [`spawn-20261101/`](spawn-20261101/) | Benchmark 04 — server spawn with players | 1.4.0 | 2026-11-01 |
| [`control-20261101/`](control-20261101/) | External cross-check of Benchmark 04 (PresentMon, stage profiles) | 1.4.0 | 2026-11-01 |
| [`spawn-20261031/`](spawn-20261031/) | Benchmark 03 — server spawn with players | 1.3.0 | 2026-10-31 |
| [`spawn-20261017/`](spawn-20261017/) | Benchmark 02 — animated Item Display spawn | 0.2.0-dev.4 | 2026-10-17 |
| [`spawn-20261016/`](spawn-20261016/) | Benchmark 01 — animated Item Display spawn | 0.1.0 | 2026-10-16 |

## What is in a folder

`raw/` holds the files exactly as DrawLess wrote them during the session, byte-for-byte: one Markdown report per recorded phase, and for automated series also the generated series summary (`README.md`, `summary.json`). Benchmarks 01 and 02 were recorded before automated series existed and contain the phase reports only.

`control-20261101/raw/` holds the external cross-check of Benchmark 04: frame-time captures recorded with [PresentMon](https://github.com/GameTechDev/PresentMon) (`presentmon/`, one CSV per 30-second capture, file names as recorded) and four DrawLess stage profiles with the master switch OFF/ON (`player-profile-*`). `off_a*`/`nomod_*` alternate DrawLess OFF and the game without DrawLess across restarts; `pm_*` alternate OFF and ON in one session.

## Verifying the files

Every `raw/` folder has a `SHA256SUMS.txt`. The per-phase hashes are also listed in the benchmark report.

```bash
cd spawn-20261101/raw && sha256sum -c SHA256SUMS.txt
```

Line endings are stored as recorded (`.gitattributes`: `* -text`), so a fresh clone reproduces the hashes on any platform.

## Limits

These are single-session recordings of one scene each on one machine. See the report for what each benchmark does and does not show.
