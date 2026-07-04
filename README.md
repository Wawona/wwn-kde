# wwn-kde

Wawona's port of the **KDE Plasma** (KWin) Wayland session + Qt/KDE apps to run
under Wawona on the Apple ecosystem and Android, App Store compliant.

> **Status: SKELETON.** flake + `registryFragment` skeleton + port plan only.
> Build stubs fail intentionally; full port is downstream.

## Delivery model

KWin is a full compositor → runs **nested** (Wawona client) or via **NixOS VM /
waypipe** for the complete Plasma desktop (heavy). Individual Qt/KDE apps
(konsole, dolphin, kate) run as direct Wawona clients with
`QT_QPA_PLATFORM=wayland`. See Wawona `docs/2026-toolkit-de-compat.md`.

## Port plan

1. Toolchain via `wwn-toolchain`; Qt6/KDE Frameworks cross-built or via VM.
2. Compliance: no JIT (QML engine considerations), no unvetted plugin loading,
   sandbox-safe dirs; prefer per-app clients over full Plasma on-device.
3. Primary-selection + xdg-decoration semantics verified against Wawona.
4. Replace `dependencies/kde/stub.nix` per platform; expose `kde-*`; register.
5. `wwn-apt` lists `kde` `status: planned` → `approved` post-review.

Convention: [wwn-* porting convention](https://github.com/Wawona/Wawona/blob/main/docs/2026-wwn-porting-convention.md).
