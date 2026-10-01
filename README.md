# Catalyst

A Windows 10 and 11 optimizer for competitive gaming and low-latency work. Catalyst brings system
tuning, debloating, CPU and interrupt affinity, hardware tools, sensors and benchmarks into one
app, and it lets you measure the result instead of guessing.

**Status:** released. Catalyst is free to use, with every feature included.

**Closed source.** This repository hosts the installer and the auto-update feed. It contains no
source code.

## Features

Catalyst is organised into the same groups as its sidebar.

### General

| Tab | What it does |
|---|---|
| Dashboard | Live CPU, GPU and RAM usage, temperatures, system specs, an "optimized" score for the General tweaks, and a history of every change you have applied. |
| Optimizer | Scans the machine (hardware, driver, installed apps, services, startup entries, devices and which tweaks are already in effect), then walks you through every relevant page. Nothing is written until you approve it. |
| Sensors | CPU, GPU, RAM and storage temperatures, clocks and loads. |
| Backup & Restore | Creates a restore point before you change anything. Each point is a Windows System Restore point plus a snapshot of every registry key Catalyst can touch, so it can be restored in place. |
| Resources | A clean GPU driver install: pick a driver package, choose which components to keep, remove the old driver, and install what is left. Also includes setup guides. |
| Fixes | One-click repairs for common problems: sign-in loops, Wi-Fi, Bluetooth, Microsoft Store and Update, re-enabling Defender, installing NVIDIA Control Panel without the Store, and Valorant anti-cheat conflicts. |

### Tweaks

| Tab | What it does |
|---|---|
| General | About 190 individual tweaks across performance, privacy, input, gaming, Windows Update, security, NVIDIA and AMD drivers, MMCSS, network, storage and audio. Each one shows what it changes, what it costs, and whether it is already applied. |
| BIOS | Opens an AMI Aptio V firmware image and edits its setup menus: unhide settings the vendor hides, change defaults, and retarget menu entries. Produces a modified image for you to flash. |
| Ram Viewer | Reads live memory timings, voltages and SPD data straight from the memory controller. Supports live timing edits on Intel 12th to 14th gen. |

### Affinities

| Tab | What it does |
|---|---|
| Device Tweaker | Builds a full affinity layout in one pass from what is plugged into each USB controller: interrupt affinity, MMCSS task affinity, network receive queues and reserved CPU sets. You approve a preview before anything is written. |
| Process Affinity | Pins running processes to chosen cores. |
| Reserved CPU Sets | Removes cores from general Windows scheduling so your game's cores see less interference. Takes effect after a reboot. |
| Interrupt Affinity | Moves device interrupts (GPU, USB, network) to chosen cores, with MSI mode and interrupt priority. |

### Debloating

| Tab | What it does |
|---|---|
| AppX Packages | Lists and removes built-in Windows apps. |
| Services | Disables unneeded services. Services that Windows sign-in depends on are protected and cannot be disabled, so a change here cannot lock you out. |
| Disk Cleanup | Clears temporary files, caches and leftover update data. |
| Autoruns | Shows and disables startup entries. |
| Scheduled Tasks | Shows and disables scheduled tasks. |
| Processes | A process manager for finding and ending background processes. |

### Network, audio, scheduling and storage

| Tab | What it does |
|---|---|
| Network Tweaks | Adapter and TCP settings that affect latency, including QoS tagging. |
| Audio Tweaks | Audio device and audio engine settings. |
| Timer Resolution | Benchmarks every timer resolution on your machine and sets the one with the lowest sleep error. |
| MMCSS | Edits the Windows multimedia scheduler profiles that games and audio threads register with. |
| Win32 Priority | Benchmarks and sets how Windows splits CPU time between foreground and background processes. |
| Storage Tweaks | File system and storage driver settings. |
| Native NVMe Driver | Installs the newer native Windows NVMe driver on supported builds, with a one-click revert. |

### Hardware

| Tab | What it does |
|---|---|
| Device Manager | Finds and disables devices you do not use, with real device icons and status. |
| Power Plans | Creates the hidden Ultimate Performance plan and edits every setting of any plan, including the ones Windows hides. |
| GPU Tuning | Core and memory clock offsets and fan control for NVIDIA GPUs. |
| Input | Mouse and keyboard settings, including turning off pointer acceleration. |
| XHCI IMOD | Reads and sets the USB controller's interrupt moderation interval, which affects how quickly mouse input reaches Windows. |

### Gaming and personalization

| Tab | What it does |
|---|---|
| Game Mode | A one-switch mode that suspends the processes you choose while you play and resumes them after. |
| Game Profiles | Per-game configuration presets. Still being filled in. |
| Wallpaper & Icons | Solid colour wallpaper, lock screen and desktop icon settings. |
| Shell Replacements | Installs alternative Start menus, taskbars and shells, each downloaded from its own project. |
| Winaero Tweaker | Appearance and Explorer behaviour settings. |

### Benchmarking

Catalyst measures the effect of every change with its own tools.

| Tab | What it does |
|---|---|
| Vulkan Benchmark | A built-in GPU benchmark scene that reports frame times and percentile lows, with optional ISR and DPC capture per CPU. |
| Game Benchmark | Attaches PresentMon to any running game and records frame time statistics. Results are saved alongside your other runs for comparison. |
| GPU Affinity | Runs the benchmark pinned to each core in turn to find the best core for the GPU interrupt. |
| Mouse Tester | Records raw mouse reports and plots report intervals and movement over a chosen time window, with statistics. |
| Network Benchmark | Measures latency, jitter and throughput for gaming, streaming and browsing. |
| Memory Benchmark | Memory latency and bandwidth, using Intel Memory Latency Checker. |
| Core Latency | Measures how long one core takes to see a value written by another, for every core pair. |
| Stress Tests | Runs y-cruncher, Linpack-Extended or Karhu RAM Test while watching per-core temperatures and Windows hardware errors (WHEA). The tools are downloaded separately. |

## How to install

1. Download `Catalyst-win-Setup.exe` from the
   [latest release](https://github.com/r3clusionn/catalyst-release/releases/latest).
2. Run it. Catalyst installs for your user account and starts automatically.
3. Accept the administrator prompt. Catalyst needs administrator rights to change system
   settings, read hardware sensors and set affinities.
4. Sign in with Discord when asked.

Installed copies update themselves. Catalyst checks for a new version every time it starts and
again every 30 minutes while it runs.

A portable build (`Catalyst-win-Portable.zip`) is also on the release page. It does not
auto-update.

### Requirements

- Windows 10 or Windows 11, 64-bit.
- An internet connection for the first sign-in. After that, Catalyst works offline for up to 72
  hours between sign-ins.
- Some hardware features (Ram Viewer, sensors, XHCI IMOD) need a kernel driver. If Memory
  Integrity (Core Isolation) is on, Windows blocks it and those features stay read-only or
  unavailable. The Dashboard has a switch for this.

## How to use

### The quick way

1. Open **Backup & Restore** and create a restore point.
2. Open **Optimizer** and press Scan. Catalyst checks your machine and shows only the changes
   that apply to it.
3. Tick what you want. Anything that removes or disables something asks you to confirm it.
4. Apply, then reboot when Catalyst says a change needs it.

### The manual way

1. Create a restore point.
2. Go through the tabs that matter to you. Every tweak card explains what it changes and what it
   costs. Changes are staged and only written when you press Apply.
3. Run a benchmark before and after (Vulkan Benchmark or Game Benchmark) to see what actually
   improved on your machine.

### Undoing changes

- **Single tweak:** turn it off and apply.
- **Everything:** open Backup & Restore and restore a point. Registry changes are reverted in
  place. A Windows System Restore point is also created when System Restore is enabled.
- **Native NVMe driver:** revert from its tab. If Windows will not boot, run
  `C:\NVMe_Backport_Temp\fix.bat` from the Windows Recovery Environment.

## Read before applying

Some tweaks trade security or stability for performance. They are marked in the app and ask for
confirmation, but you should know what they do:

- **Security:** turning off Defender, UAC, Memory Integrity, Virtualization Based Security or CPU
  vulnerability mitigations makes the system easier to attack. Some anti-cheats (Valorant,
  FACEIT) require Memory Integrity.
- **Windows Update:** turning it off stops security patches until you turn it back on.
- **RAM timing edits and GPU clock offsets** apply to the running system. An unstable value can
  freeze or restart the PC. RAM edits are lost on reboot.
- **BIOS images** are written by you, not by Catalyst. Flashing a bad image can stop the board
  from booting. Keep a copy of the original.

Results depend on your hardware. Benchmark your own system before and after rather than
assuming a tweak helps.

## Privacy

Signing in uses Discord. Catalyst stores your Discord ID and username, a hardware ID for this PC,
the Catalyst version, your last launch time and the IP address it was launched from. This is used
for account access and to block abuse. Catalyst does not upload your files, settings or benchmark
results.

## Support

Report bugs and requests in the [Issues](https://github.com/r3clusionn/catalyst-release/issues)
tab. Include your Windows version, the Catalyst version (shown in the sidebar) and the log at
`%LocalAppData%\Catalyst\update.log` if the problem is with installing or updating.

## License

Free to use. Proprietary, all rights reserved. Redistribution and modification are not permitted.
