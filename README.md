# reactos-nitro

**reactos-nitro is an unofficial patch set for [ReactOS](https://reactos.org).** It is not affiliated with or endorsed by the ReactOS project. ReactOS is a trademark of the ReactOS project.

> **Do not report problems from this build to the ReactOS project.** Report them here, in this repository's issues.
>
> Like ReactOS itself, this is alpha-quality software. Don't use it on a machine or disk holding data you care about.

reactos-nitro is a large set of fixes and features maintained on top of upstream ReactOS master. Each release ships:

- **the patch series**: one patch per topic, plus the exact upstream ReactOS commit it applies to;
- **build scripts** that apply the series to a clean upstream checkout and build the ISOs;
- **ready-to-install ISOs** for amd64 (with WoW64) and i386;
- **the full source tree** of the release, tagged in the [development fork](https://github.com/tomassrnka/reactos).

## Status

Pre-release. The first release, `reactos-nitro-2026.10.1`, is in preparation. Until it's published, there are no downloads here.

## Highlights

Over 520 fixes and several feature tracks on top of upstream ReactOS:

- **32-bit Windows programs on 64-bit ReactOS (WoW64).** Total Commander and Firefox ESR, each in 32-bit and 64-bit builds, run side by side in one session. Upstream ReactOS has no WoW64.
- **NTFS read/write**, with a new driver built on the Linux kernel's `fs/ntfs` (imported from Linux v7.3-rc6), plus journal and power-cut recovery. NTFS is the default file system for new installs.
- **Btrfs**: WinBtrfs 1.10 (upstream ships 1.8.1).
- **Multi-processor support on x86 and amd64**, installed by default on ACPI machines. It is tested from 1 to 16 vCPUs, with multi-hour soaks on AMD and Intel hosts.
- **Smoother desktop.** A shadow framebuffer makes window dragging smooth at a fraction of the CPU cost. USB tablet polling and pointer fixes also help.
- **Networking**: a reworked receive path and dozens of TCP/IP, AFD and Winsock fixes.
- **Setup and user profiles**: the setup program preselects NTFS. The C:\Users layout includes Windows-style legacy folder links, and profile deletion works.
- **Kernel and memory manager hardening**: commit charging with a commit limit, plus many Mm, cache-manager and scheduler fixes.
- **Desktop and tools**: LCD text rendering, bundled open fonts, crash reports with a Windows-style dialog, and Disk Management.

A full list of changes, one line per fix, is in [CHANGELOG.md](CHANGELOG.md) (draft for the first release).

## Known limitations

- WoW64 is amd64 only.
- The Firefox sandbox starts on 64-bit, but its restrictions are **not** enforced on ReactOS. 32-bit Firefox runs with its sandbox disabled.
- Some 32-bit applications leave redraw artifacts when dragged over other windows.
- Firefox ESR 140 and later need components that ReactOS does not provide yet. ESR 128 is the tested version.
- Everything in upstream ReactOS's own list of known issues also applies.

## Identifying a reactos-nitro build

The desktop shows `ReactOS (Nitro) - <version>`. The About dialog also says *"Unofficial build, not supported by the ReactOS project"*.

## Licence and credits

reactos-nitro is distributed under the same licences as ReactOS: mainly GPL-2.0-or-later, with per-file licences kept as they are in the source. Upstream copyright notices are kept intact.

Credit goes to:

- the [ReactOS project](https://reactos.org) and its contributors, whose operating system this builds on;
- the authors of the Linux kernel's `fs/ntfs` driver;
- [WinBtrfs](https://github.com/maharmstone/btrfs) by Mark Harmstone;
- the [Wine project](https://www.winehq.org), whose code ReactOS and this patch set reuse.
