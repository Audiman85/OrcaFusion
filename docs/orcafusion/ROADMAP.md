# OrcaFusion — initial development milestones

## Repository status
Official OrcaSlicer fork renamed to `Audiman85/OrcaFusion`. Current source is an upstream fork; the tasks below are **not yet implemented**.

## Milestone 1 — Branding and launch identity
- [ ] Add approved combined logo to `resources/orcafusion/branding/orcafusion-logo.png`
- [ ] Add approved standalone avatar to `resources/orcafusion/branding/orcafusion-avatar.png`
- [ ] Add generated Windows `.ico` and size variants
- [ ] Replace startup splash branding; display OrcaFusion version, build channel and build identifier sourced from the build system
- [ ] Replace desktop app icons, installer and About page visuals while preserving upstream attributions
- [ ] Test logo readability in dark and light modes

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

## Future backlog
- [ ] Custom theme editor (lower priority)
- [ ] Resin slicing research only, excluded from initial FDM scope

**Note:** GitHub Issues are currently disabled on this repository. Re-enable them under GitHub repository Settings > General > Features if issue tracking is desired.
