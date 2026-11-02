# Future Roadmap — Windows Multi-Host Ping Monitor

This is a **planned feature list**, not a claim that features are already implemented. Priorities may change after Windows field testing.

## v1.0 — Current
- Windows 10/11 Tkinter multi-host ICMP monitoring (up to 50 hosts)
- Per-packet sequence, RTT, TTL, size and UP/DOWN
- Rolling last-20 packet loss and min/avg/max latency; lifetime counters
- Host save/load, start/stop, detail window, PyInstaller EXE build
- RTT precision limited by Windows ping.exe output

## v1.1 — Reliability and usability
- Windows 10/11 runtime tests, error handling and packaging validation
- Better timestamps, scrollbars, sorting and status color consistency
- Save/restore selected hosts and monitoring interval; import/export host list
- Fix or document stop/restart race conditions and detail-window refresh behavior

## v1.2 — Precision and probing
- Evaluate Windows ICMP API to obtain fractional-millisecond RTT where supported
- Document that microsecond display does not guarantee microsecond accuracy
- IPv4/IPv6 improvements and localized Windows compatibility
- Configurable timeouts, interval, threshold alerts and retry policy

## v1.3 — Visibility and history
- Live RTT charts, per-host trend history
- CSV export with timestamp, host, sequence, latency and status
- Separate last-20 versus lifetime metrics and batch-20 summaries
- Optional sound and desktop notifications with alert cooldown

## v2.0 — ISP operations
- TCP connect port checks as an opt-in separate mode, not equivalent to ICMP
- Host grouping, labels, tags and saved monitoring presets
- Optional per-interface/source address selection where OS allows
- Stable long-running monitoring and performance testing with 50 hosts
- Optional signed release artifacts, checksums and CI smoke tests

## Validation checklist
- Exercise DNS failure, host blocked ICMP, host removal while running, network adapter changes, IPv6, timeout handling, low RTT and unresponsive targets.
- Verify executable on clean Windows 10 and 11; check Windows Defender/SmartScreen handling and avoid claiming security certification.
- Keep secrets, private monitoring targets and local data out of the repository.