# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-10-15

### Added

- Visual Studio 2022 solution (`CppTemplateGui.sln`) containing all 8 UI projects, x64, Debug + Release
- One project per UI: `KellUI`, `MaotawTerminal`, `MenuSense_Rainbow`, `inabooUI`, `maotaw_ui`, `phantom_ui`, `playhookUI`, `spectraUI`
- GitHub Actions **Build** workflow: every push builds all 8 executables and uploads them as a downloadable artifact
- GitHub Actions **Release** workflow: pushing a `v*` tag builds the exes and publishes a GitHub Release with all executables attached
- `CHANGELOG.md` so every release ships categorized change notes (Added / Changed / Removed / Fixed / Improved)

### Changed

- Source files moved from the repository root into per-project folders under `src/<Name>/`
- Build output now goes to `bin/x64/<Debug|Release>/` instead of `build/`
- README rewritten: solution layout, Visual Studio build steps, releases, and release process

### Removed

- VS Code build/debug configs (`.vscode/`) — replaced by the Visual Studio solution
- Loose per-file `cl.exe` command lines — replaced by MSBuild project files
- Old `build/` output convention

### Fixed

- `inabooUI.cpp` did not compile at all: `App::WindowProc` declaration was missing its `HWND` parameter
- `inabooUI.cpp` scrollbar math mixed `int` and `float` in `std::max` / `std::clamp` calls
- Duplicate `WIN32_LEAN_AND_MEAN` / `NOMINMAX` macro definitions between project files and sources (C4005 warnings)

### Improved

- All 8 UIs now compile and link cleanly as one `msbuild CppTemplateGui.sln` invocation
- Sources are compiled with `/utf-8`, so special characters (— • ° ×) in the UI text render and compile correctly

[Unreleased]: https://github.com/sapkotasachin064-beep/C---Template-Gui/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/sapkotasachin064-beep/C---Template-Gui/releases/tag/v1.0.0
