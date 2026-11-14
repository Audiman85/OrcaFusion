# OrcaFusion branding assets

OrcaFusion is the working name for the cross-manufacturer FDM slicer fork.

## Approved visual direction
- Default UI: dark charcoal with teal accents; light mode selectable.
- Logo: orca silhouette with white markings, teal orbital swoosh and stacked 3D-print layers.
- Wordmark: **Orca** over **Fusion** at balanced relative scale.

## Assets for integration

| Asset | Destination | Purpose |
|---|---|---|
| Combined logo | `resources/orcafusion/branding/orcafusion-logo.png` | About dialog, startup/splash screen, website and documentation |
| Standalone orca avatar | `resources/orcafusion/branding/orcafusion-avatar.png` | Main app icon, GitHub avatar, window/taskbar icon, shortcut |

Source artwork is prepared in the conversation as PNGs and awaits binary upload to the destinations above. It has **not** yet been wired into app resources or a compiled build.

## Implementation checklist
- [ ] Commit the approved transparent PNG image files at the locations above.
- [ ] Generate application-size icons (16, 24, 32, 48, 64, 128, 256 px) and an ICO file from the avatar master.
- [ ] Audit existing OrcaSlicer branding/resource references before replacing any; preserve upstream license notices and attribution.
- [ ] Add icon to Windows executable, taskbar, title bar, About window, splash/loading screen and installer.
- [ ] Add the combined logo to the About dialog, first-run interface, app documentation and website.
- [ ] Check both light and dark modes; avoid very dark wordmark on dark backgrounds (use a high-contrast variant).
- [ ] Review branding/trademark considerations and make it clear OrcaFusion is an independent fork.

## UI priorities
1. Resizable, independently scrollable settings panels; no cut-off labels.
2. Windows HiDPI and text scaling tests, including 1366×768 at 125%, 150%, 175%, and 200% scaling.
3. Default dark teal theme with accessible preset themes, optional light mode; custom theme editor later.
4. Hover-tooltips for slicer settings; clicking a label or description opens its exact Wiki explanation **directly in the browser**, with no intermediate preview.
5. Preserve all existing printer support while extending cross-manufacturer FDM integrations. No Rinkhals or firmware flashing for Kobra S1/Kobra 3.

Resin printer slicing remains out of initial scope.
