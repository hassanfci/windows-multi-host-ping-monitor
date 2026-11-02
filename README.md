# Windows Multi-Host Ping Monitor v1.0

Windows 10/11 graphical continuous multi-host ping monitor built in Python Tkinter. No admin privileges necessary for ordinary ping.

## Features

- Add/remove up to 50 hosts; list saved to `%APPDATA%\MultiHostPingMonitor\hosts.json`
- Start All / Stop All, one ICMP echo per target per cycle
- Per-packet SEQ, host, size, TTL, latency and UP/DOWN
- Dashboard: last RTT, last-20 packet loss, avg/min/max RTT, lifetime sent/loss
- Select host for packet details; double-click to open a larger detail window
- Adjustable interval and packaged single-file EXE build

## Run and build

1. Install Python 3 on Windows, including Tkinter.
2. Run `Run_Python.bat`.
3. Add your hosts and click **Start All**. Double-click any host for an expanded per-packet view.
4. For an EXE, run `Build_EXE.bat` (requires internet access to install PyInstaller). The EXE will be under `dist\Multi-Host-Ping-Monitor.exe`.
5. Copy that **one-file EXE** to another Windows 10/11 PC; Python is not required.

## Precision and limitations

- Uses Windows **ping.exe** which reports integer milliseconds or `<1ms`; microsecond precision is **not** available and `<1ms` is treated as 0.5ms only for the aggregated calculations.
- Tested by Python syntax compilation, **not** runtime tested on Windows in this environment.
- The reply parser expects **English-language Windows ping output**. Other Windows display languages may require parser updates.
- Monitoring is sequential *per host*, but each host runs in a parallel worker thread.
- Interval is the desired start-to-start interval; a slow ping/timeout may extend it. Per-packet `-w 1000` limits ordinary ping waits to 1 second.
- Last-20 stats are a *rolling window*, not a batch reset every 20 packets; lifetime totals continue accumulating.
- Stop/Start retains previous totals (close/relaunch resets them).
- ICMP may be blocked on some networks; DOWN doesn't necessarily mean an application or TCP port is down.
- The app checks **host ICMP reachability**, not TCP port availability.

## Security

Host strings are validated and passed as subprocess arguments without a shell. No profiles or private network addresses are uploaded anywhere. Use only on networks and hosts you are authorized to monitor.

## Future plans
See [ROADMAP.md](ROADMAP.md) for planned v1.1–v2.0 functionality, including Windows ICMP API evaluation, graphs, CSV logging, configurable alerts, and optional TCP port checks. These features are not included in v1.0.