# OrcaFusion — splash screen and About/build information

## Final approved splash artwork — LOCKED

**The FIRST dramatic glowing OrcaFusion splash preview is the final visual design.**
Use the first preview with the **wide horizontal OrcaFusion wordmark**, bright cyan/teal edge highlights, swooping teal underline, large black-and-white orca above stacked teal printing layers, atmospheric dark teal background, and illuminated hexagonal floor. The user explicitly rejected the **second/smoother animation preview's redesigned stacked "Orca / Fusion" logo**, because it lost the original design qualities.

**Preserve the original logo artwork, proportions, lettering, orca shape, layer stack, teal sweep, colors and composition.** Future previews, assets and implemented animation must *not regenerate, simplify, reword, rearrange, or replace the brand mark*. The existing app/avatar branding remains unchanged; this decision is specific to the startup splash.

**Animation:** Smooth, slow continuous pulse of the glow/halo around the ORIGINAL logo and wordmark only. Generate additional glow intensity/opacity frames or animate an overlay—not alternate logo drawings. Keep positions fixed. The loading bar and status remain real UI, not baked into background art. The old second preview is rejected as a design reference.

**Asset status:** The first preview is approved as visual reference, but the isolated original glowing logo and background have **not yet** been committed as usable separate splash PNG assets. Extract/redraw from that exact first preview before integration, and verify the resulting art matches it; do not claim final asset integration is complete.

## Dark-background orca visibility correction (November 14, 2026)

First desktop test feedback: the remaining upstream `OrcaSlicer` logo showed an orca too dark for a dark background. Dark-only SVG fixes have been committed for:
- `resources/images/splash_logo_dark.svg`
- `resources/images/OrcaSlicer_horizontal_dark.svg`
- `resources/images/OrcaSlicer_about_dark.svg`

The near-black orca fills have been replaced with high-contrast whites, with the eye contrast and icon tile adapted for dark mode. The teal logo accents and light-theme SVGs remain unchanged. **This is a targeted correction to visible upstream/fallback branding, not replacement of the locked FIRST glowing OrcaFusion splash design.**

A new Windows build is required before these revised SVGs can be tested. Existing downloaded portable builds **will not update themselves**. The currently implemented OrcaFusion splash renderer separately loads `resources/orcafusion/branding/orcafusion-logo.png` until the approved isolated splash-only assets are packaged; do not misrepresent this SVG fix as completion of the final OrcaFusion splash.

## Dark-background logo contrast fix (first Windows feedback)
- The existing transparent full-logo fallback `resources/orcafusion/branding/orcafusion-logo.png` uses **dark “Orca” text** above the teal “Fusion” word, which is difficult to read on the splash's nearly black background.
- The first Windows x64 test user requested **white “Orca” lettering**. The splash renderer now changes only the dark pixels in the known “Orca” text region to an off-white shade during fallback PNG loading; the original illustration, transparent background, and teal “Fusion” lettering remain unchanged. Runtime fix commit: `174da1e`. This is deliberately not applied to the final splash-only logo if/when provided.
- The legacy `resources/images/splash_logo_dark.svg` also has its formerly dark orca silhouette paths changed to white, committed as `d365246` for contrast wherever that SVG is used.
- **Validation pending**: confirm actual startup appearance in a new Windows x64 build, avoid image artifacts, and verify the original glowing splash-specific logo remains the ultimate design target. Source changes alone do not establish visual/runtime success.

## Approved branding

The **first** dramatic dark-teal/glowing logo preview is the **final selected design for the splash screen only**. The second, smoother-animation preview's modified logo is not approved. Preserve the previous standalone orca avatar for app/window/taskbar icons and the existing full logo for ordinary branding. The splash-only artwork is not yet uploaded as isolated, text-free layers. The generated preview has baked-in version/loading/progress text and must **not** be used directly behind live UI because that would duplicate information.
Use the **actual uploaded OrcaFusion artwork**, never a generic or AI-search substitute.
- Full logo: `resources/orcafusion/branding/orcafusion-logo.png` (the approved black/teal orca plus stacked Orca/Fusion lettering)
- App/avatar icon: `resources/orcafusion/branding/orcafusion-avatar.png`
- Windows icon: `resources/orcafusion/branding/orcafusion.ico`

## Splash screen (startup)

### Locked layout, top to bottom
1. Dark navy/black background with subtle teal lighting, futuristic teal glow, and understated lower-edge hexagonal/floor texture. Target desktop splash aspect ratio **16:9**, presently **720 × 405 DIP**.
2. Centered, splash-only glowing orca+OrcaFusion art, proportional, not cropped; artwork includes the brand name so **no second app-name heading**.
3. Version centered below art. Stable: `Version X.Y.Z` only; beta/development: semantic version with channel.
4. Short Git commit (e.g. `Commit abc1234`) **for beta/development only**, never stable.
5. Teal progress track and real progress percentage; progress is not a decorative animation or hardcoded fake value.
6. Below the progress bar, dynamic initialization messages sourced from actual app startup phases (e.g. Loading configuration, Loading printer profiles, Initializing interface). No fixed timer or artificial wait.
7. When the startup process is ready, close the splash automatically and show OrcaFusion.
8. **Animated glow**: subtle pulsing teal glow around the splash-only orca emblem and wordmark, ~2.5 seconds per cycle. Animate the glow opacity/intensity rather than zooming the logo; keep text crisp, progress based on real stages, and loading labels static/readable. Use efficient timed UI refreshes only while splash is visible; cap refresh frequency and stop immediately when it closes. Respect reduced-motion preference (where supported), offer an option to disable animation, and show static glow on lower-resource/Lite installations. Never delay startup for the animation.

### Asset separation
- `resources/orcafusion/branding/orcafusion-splash-background.png`: future text-free background resembling the approved preview; no text or progress bar baked in.
- `resources/orcafusion/branding/orcafusion-splash-logo.png`: future isolated version of the **first, original glowing** OrcaFusion splash emblem/wordmark from the approved first preview, with transparency; used only on splash.
- `resources/orcafusion/branding/orcafusion-logo.png`: existing approved logo, fallback until the two splash-specific assets exist.
- `resources/orcafusion/branding/orcafusion-avatar.png` and `orcafusion.ico`: **unchanged**, for app/taskbar/installer icons.
- Always show the actual approved **full OrcaFusion logo** (preserve aspect ratio and alpha). The logo already contains the name; **do not render a second `OrcaFusion` text heading beneath or beside it**.
- **Stable releases:** beneath the logo display **only the friendly version number**, e.g. `Version 1.0.0`. Do **not** show a duplicate app-name heading, channel, build number, commit SHA or build date on the splash.
- **Development and beta releases:** display the semantic version with channel (e.g. `0.1.0-dev` or `0.9.0-beta.1`); optional concise build identifier for internal builds.
- Continue the existing progress/loading indication. No artificial delay.
- Keep labels and imagery visible on dark and light themes, including 125–200% Windows DPI and 1366x768 displays.
- If the logo cannot be loaded, show plain OrcaFusion text instead of a blank/crashing window.

## Help → About OrcaFusion (all release channels)
The About dialog **always shows** these fields, including on stable releases. Use the logo itself as the visible brand heading and do not duplicate the application name as a second large heading; the formal app name can remain in the information/details fields:
1. Application name: **OrcaFusion**
2. App version: e.g. `1.0.0`
3. Release channel: `Stable`, `Beta` or `Development`
4. Build number: CI/build system run identifier
5. Git commit: precise source revision (short SHA in UI, full SHA in copyable details)
6. Build date/time: ISO 8601 UTC from the build pipeline
7. Original OrcaSlicer credits, copyright notices and required open-source license attribution

Provide a **Copy build details** action for diagnostics. Include the full version/build info in diagnostic output regardless of channel. If metadata is missing, display `Unavailable` rather than an invented value.

## Build-metadata wiring
- Upstream already exposes Git SHA in `src/slic3r/GUI/BuildCommit.hpp` via `build_commit_label` and derives it through `src/slic3r/GitCommitHash.cmake`.
- Upstream version `SoftFever_VERSION` is currently defined in `version.inc`. Introduce an OrcaFusion-specific version/channel in a controlled change without silently migrating profile directories.
- Extend CMake/CI to generate build number and UTC timestamp once per compiled build; derive commit from the source revision.
- Do not hardcode example values such as `1.0.0` or `#0001` as live metadata.

## Integration roadmap
- [x] Upload approved PNG / ICO branding to `resources/orcafusion/branding`
- [x] Windows resource script points to OrcaFusion icon and product description
- [x] Locate upstream splash source: `src/slic3r/GUI/GUI_App.cpp`, `SplashScreen`
- [x] Locate upstream About source: `src/slic3r/GUI/AboutDialog.cpp`
- [x] Source splash renderer reads `orcafusion-splash-logo.png` when available, falling back to approved `orcafusion-logo.png`; optional background supported
- [ ] Upload isolated splash-specific glowing logo and text-free background from chosen preview
- [x] Splash uses build-time version and hides commit on non-prerelease versions; short commit shown for prerelease builds
- [ ] Introduce OrcaFusion-specific version/channel (currently based on upstream `SoftFever_VERSION`)
- [ ] Generate build number and timestamp in CI/CMake and expose to C++
- [ ] Implement all About fields and copy-details action
- [ ] Validate light/dark themes, screen scaling, startup performance, packaging
- [ ] Compile and validate a real Windows build

**Implementation status:** initial splash rendering logic has been changed in `src/slic3r/GUI/GUI_App.cpp` (commit `8eb6ed7`), but **not compiled or tested**. The extra splash-only artwork still needs to be isolated and committed, and the About dialog/CI metadata pipeline is not yet updated.
