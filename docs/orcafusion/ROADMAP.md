# OrcaFusion — initial development milestones

## Repository status
Official OrcaSlicer fork renamed to `Audiman85/OrcaFusion`. Current source is an upstream fork; the tasks below are **not yet implemented**.

## Milestone 1 — Branding and launch identity
- [x] Add approved combined logo to `resources/orcafusion/branding/orcafusion-logo.png`
- [x] Add approved standalone avatar to `resources/orcafusion/branding/orcafusion-avatar.png`
- [x] Add generated Windows `.ico` and size variants
- [ ] Replace startup splash branding; display OrcaFusion version, build channel and build identifier sourced from the build system
- [ ] Replace desktop app icons, installer and About page visuals while preserving upstream attributions
  - [x] Windows executable resource now references `orcafusion.ico` and uses the OrcaFusion product name (commit `63910da`)
  - [ ] Verify Windows executable after compilation and continue with installer, splash and About visuals
- [ ] Test logo readability in dark and light modes
- [ ] Add gently pulsing teal glow to splash-only logo and wordmark (roughly 2.5 s cycle), with no layout movement; avoid continuous CPU/GPU-intensive redraws
- [ ] Reduced-motion/disable-animation option and static fallback; progress and loading messages remain independent and truthful

See [branding specification](./BRANDING.md) and [startup/build specification](./SPLASH_AND_BUILD_INFO.md).

## Milestone 2 — UI layout and Windows scaling
- [ ] Audit dialogs and settings panes for fixed dimensions and clipped text
- [ ] Ensure individual settings sections scroll independently
- [ ] Provide user-adjustable sidebar width and retain layout preferences
- [ ] Test Windows DPI 100%, 125%, 150%, 175%, and 200%; test 1366x768 and larger displays
- [ ] Implement dark teal default, light option and high-visibility presets
- [ ] Hover setting tooltip is brief; clicking the setting name/description opens the **exact Wiki explanation directly** in the browser (no preview, no generic homepage)

## Milestone 3 — Cross-manufacturer FDM support
- [ ] Keep supported upstream printers
- [ ] Develop stock-firmware integrations for Anycubic Kobra 3 and Kobra S1, validate separately
- [ ] No Rinkhals, no bootloader changes, no required printer firmware modification
- [ ] Expand to other brands using modular printer connection adapters
- [ ] Integrate mature features from compatible open source slicing projects with correct licenses/credits

## Milestone 4 — Performance and optional Lite installation profile
- [ ] Benchmark cold start, memory consumption, interactive responsiveness and slicing speed on lower-end Windows hardware
- [ ] Keep **Full** installation selected by default; offer **Lite** as an optional installer feature set, not a separate slicer engine
- [ ] Preserve identical core geometry, profiles, G-code safety, slicing correctness, print quality and machine compatibility in Lite
- [ ] Lite defaults: turn off splash animation, reduce costly live 3D preview effects/quality, limit background tasks, and disable optional online/dashboard integrations where practical
- [ ] Use lazy loading/on-demand components and optional assets; identify costly dependencies with profiling before removal
- [ ] Provide user controls to re-enable optional features without reinstalling where feasible
- [ ] Test representative low-end hardware and all supported printers; never suggest Lite supports hardware that fails minimum OpenGL/OS/runtime requirements


## Compatibility research — 32-bit Windows (experimental)
- [ ] Evaluate feasibility of an **optional OrcaFusion Lite x86 (32-bit)** build; do not imply support until verified
- [ ] Audit all build dependencies, vendor SDKs, native network plugins, WebView, graphics stack and Windows packaging for x86 availability
- [ ] Prototype an isolated x86 build only after Full and 64-bit Lite are reliable; do not alter their release configurations
- [ ] Benchmark realistic address-space limitations and memory pressure with larger FDM models and multicolor jobs
- [ ] Confirm actual OS, CPU and OpenGL requirements; older machines may remain incompatible even if x86 binaries compile
- [ ] Require equivalent G-code correctness and print safety before release, otherwise document unsupported hardware

Current upstream OrcaSlicer Windows build flow explicitly supports **x64 and ARM64**, not x86; 32-bit is a research goal, not a promised edition.

## Future backlog
- [ ] Custom theme editor (lower priority)
- [ ] Resin slicing research only, excluded from initial FDM scope

**Note:** GitHub Issues are currently disabled on this repository. Re-enable them under GitHub repository Settings > General > Features if issue tracking is desired.
