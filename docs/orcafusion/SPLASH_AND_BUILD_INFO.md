# OrcaFusion — splash screen and About/build information

## Approved branding
Use the **actual uploaded OrcaFusion artwork**, never a generic or AI-search substitute.
- Full logo: `resources/orcafusion/branding/orcafusion-logo.png` (the approved black/teal orca plus stacked Orca/Fusion lettering)
- App/avatar icon: `resources/orcafusion/branding/orcafusion-avatar.png`
- Windows icon: `resources/orcafusion/branding/orcafusion.ico`

## Splash screen (startup)
- Always show the actual approved **full OrcaFusion logo** (preserve aspect ratio and alpha).
- **Stable releases:** display **only the friendly version number**, e.g. `Version 1.0.0`. Do **not** show channel, build number, commit SHA or build date on the splash.
- **Development and beta releases:** display the semantic version with channel (e.g. `0.1.0-dev` or `0.9.0-beta.1`); optional concise build identifier for internal builds.
- Continue the existing progress/loading indication. No artificial delay.
- Keep labels and imagery visible on dark and light themes, including 125–200% Windows DPI and 1366x768 displays.
- If the logo cannot be loaded, show plain OrcaFusion text instead of a blank/crashing window.

## Help → About OrcaFusion (all release channels)
The About dialog **always shows** these fields, including on stable releases:
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
- [ ] Wire full approved PNG into actual splash renderer
- [ ] Implement channel-specific splash version visibility
- [ ] Generate build number and timestamp in CI/CMake and expose to C++
- [ ] Implement all About fields and copy-details action
- [ ] Validate light/dark themes, screen scaling, startup performance, packaging
- [ ] Compile and validate a real Windows build

**Implementation status:** branding sources uploaded and Windows executable-resource references changed; splash and About specifications updated here, but these runtime features are not yet implemented or compiled.
