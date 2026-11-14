# OrcaFusion — first Windows test build

## Status (2026-11-14)
The existing upstream workflow `.github/workflows/build_all.yml` already supports both **push** and **workflow_dispatch**. Its Windows matrix builds x64 (and, on a normal main-branch push, ARM64), using the reusable workflows `build_check_cache.yml` and `build_orca.yml`.

The GitHub repository Actions runs endpoint returned **zero workflow runs** when inspected on 2026-11-14. **No Windows binary or validated installer is currently available.** This can occur when Actions has not been enabled or no runs were created; inspect repository Settings → Actions before concluding the cause.

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
