# OrcaFusion — first Windows test build

## First real build results — November 14, 2026

**GitHub Actions run:** [Build all #43601931230](https://github.com/Audiman85/OrcaFusion/actions/runs/43601931230)  
**Source revision:** `8ea8f61c8081d174b31625bbc47cc4f4780ee0f5`  
**Overall workflow conclusion:** `failure` (does **not** mean Windows x64 failed).

Verified job results from GitHub:
- **Build Windows x64 / Build OrcaSlicer: SUCCESS.**
- Windows x64 installer creation, Windows x64 ZIP upload, portable upload and MSIX upload steps: **SUCCESS**.
- Windows x64 unit tests: **SUCCESS**.
- Windows ARM64 build and unit tests: **SUCCESS**.
- Linux x86_64 and aarch64 builds/tests: **SUCCESS**.
- macOS x86_64 and arm64 build jobs: **CANCELLED**; downstream macOS universal build was skipped. The cancelled job logs were not retrievable through the available API, so the reason for the overall red conclusion is **not verified**.
- No job in the 50-job summary returned conclusion `failure`.

Relevant downloadable artifacts on the workflow-run page (all are still labeled upstream `OrcaSlicer`, version `2.6.0-dev`):
- `OrcaSlicer_Windows_V2.6.0-dev_x64_portable` (artifact ID `14120712098`, ~203 MB compressed)
- `OrcaSlicer_Windows_V2.6.0-dev_x64` (artifact ID `14120826767`, ~160 MB compressed)
- `OrcaSlicer_Windows_MSIX_V2.6.0-dev_x64` (artifact ID `14120906042`, ~204 MB compressed)

**For the first Windows test**, download the **x64 portable** artifact from the run summary, extract it completely and start the bundled app executable. Avoid ARM64 packages on the Ryzen 5 4500U (x86-64). Keep existing OrcaSlicer installation and profiles safe; this development fork retains some upstream application identity/profile paths and can potentially share configuration directories. Back up profiles or test on a separate Windows user before launching. Windows SmartScreen or other security dialogs may appear for untrusted/unsigned development artifacts; do not bypass them without independently verifying the artifact provenance.

**Important:** Successful compilation is not confirmation of correct real-world appearance. The approved first glowing splash logo layers are not yet packaged, and this build may show the fallback logo and an early halo implementation rather than the final visual. Do not consider branded UX, Lite installer or printer connectivity complete.

## Status (2026-11-14)
The existing upstream workflow `.github/workflows/build_all.yml` already supports both **push** and **workflow_dispatch**. Its Windows matrix builds x64 (and, on a normal main-branch push, ARM64), using the reusable workflows `build_check_cache.yml` and `build_orca.yml`.

Historical note: before enabling Actions, the repository reported zero workflow runs. The first manual build above has since completed and produced Windows x64 artifacts; hands-on execution/visual validation is still outstanding.

## How to start the first build from GitHub
1. Open [Actions](https://github.com/Audiman85/OrcaFusion/actions) and check whether repository Actions are enabled. If disabled, enable the appropriate actions in Settings → Actions → General.
2. Open **Build all** in Actions and choose **Run workflow** on branch `main`. Leave **Only build dependencies** unchecked.
3. Inspect the **Build Windows x64** job and its dependencies; if the job fails, collect the failed step and build logs rather than downloading an incomplete package.
4. Once a Windows x64 build succeeds, use the uploaded build artifacts in that run. Treat them as **development builds**, not signed production releases.
5. Test on the reported AMD Ryzen 5 4500U PC and confirm version/commit label, branded splash artwork fallback, loading progress, animation performance and no startup crash.

## Splash-specific test checklist
- [ ] Original FIRST approved glowing splash design is present (splash-only assets not committed yet)
- [ ] App avatar/icon and ordinary brand logo unchanged
- [ ] Smooth 2.5-second teal halo, no logo movement or image alternation
- [ ] Stable version suppresses commit; prerelease shows seven-character commit
- [ ] Real progress and loading messages; no duplicated text painted into background image
- [ ] High DPI 100%, 125%, 150%, 200% without clipped content
- [ ] Startup closes splash reliably; timer stops on destruction
- [ ] Resource loading works from packaged Windows install location
- [ ] Low-resource/reduced-motion fallback (not yet implemented)
- [ ] Record Windows executable hash, exact commit, action run URL and observed issues

## Known development limitations
- The logo-isolation artwork step is incomplete. Renderer currently falls back to `resources/orcafusion/branding/orcafusion-logo.png` until splash-specific PNGs are committed.
- The halo code is committed but has not yet been compiled or profiled.
- This repository's upstream workflow is a full multi-platform build, so triggering it may use substantial GitHub Actions minutes.
- A release installer or Lite profile does not exist yet. Never claim one is ready before build validation.
