# C++ Direct2D UI Collection

A collection of 8 standalone Direct2D / DirectWrite menu UI templates for Windows, written in C++17 with the Win32 API and packaged as a **Visual Studio 2022 solution**.

> **Credits & attribution:** All 8 UI source files in `src/` originate from the [**maotaw-cmd/c-**](https://github.com/maotaw-cmd/c-) repository. Full credit for the UI code goes to its original author. This project only adds the Visual Studio solution, build automation and packaging around that code and claims no ownership over it. See [Credits](#credits) below for details.

## Requirements

- Windows 10/11
- Visual Studio 2022 with the **Desktop development with C++** workload (MSVC v143 + Windows SDK)
- Direct2D / DirectWrite (included with the Windows SDK)

No local compiler? Use the GitHub Actions build (see below) — GitHub builds the executables for you.

## Repository layout

```
CppTemplateGui.sln              Visual Studio solution (x64, Debug + Release)
src/
  KellUI/                       Each UI is its own Visual Studio project
    KellUI.vcxproj
    KellUI.vcxproj.filters
    KellUI.cpp
  MaotawTerminal/
  MenuSense_Rainbow/
  inabooUI/
  maotaw_ui/
  phantom_ui/
  playhookUI/
  spectraUI/
.github/workflows/build.yml     CI: builds all 8 exes on every push
```

## UIs

| Project | Description |
|---------|-------------|
| `KellUI` | Dark transparent full-width Direct2D menu with Aimbot/Visuals controls, color picker, config system |
| `MaotawTerminal` | Custom teal terminal with built-in editor, syntax highlighting, context menu, tray integration |
| `MenuSense_Rainbow` | MenuSense-style UI with animated rainbow top bar, sidebar navigation, config profiles |
| `inabooUI` | Transparent black menu with connected particles, color picker, config manager |
| `maotaw_ui` | Screenshot-style ragebot UI with collapsible sidebar, breadcrumb navigation |
| `phantom_ui` | Purple neon reference UI with animated background, skeleton preview, config system |
| `playhookUI` | Compact purple UI with hotkey combos (Ctrl+Alt+Shift), RGB color picker, ESP colors |
| `spectraUI` | Spectra UI with blur effects, companion windows, watermark overlay, keybind/spectator lists |

## Building in Visual Studio 2022

1. Open `CppTemplateGui.sln`
2. Select the configuration **Release | x64** in the toolbar
3. Build a single UI (right-click its project → Build) or everything at once (Build → Build Solution)
4. Executables land in `bin\x64\Release\` — e.g. `bin\x64\Release\KellUI.exe`

Or from a Developer Command Prompt:

```batch
msbuild CppTemplateGui.sln /m /p:Configuration=Release /p:Platform=x64
```

## Building on GitHub (no local setup needed)

Every push to `main` automatically builds all 8 executables on GitHub:

1. Open the repository's **Actions** tab
2. Open the latest **Build** workflow run
3. Download the **CppTemplateGui-exe-x64** artifact — it contains all eight `.exe` files

You can also trigger a build manually: **Actions → Build → Run workflow**.

## Releases

Every versioned release ships the ready-to-run executables as release assets:

1. Open the repository's **Releases** page
2. Download the `.exe` you want from the latest release (all 8 UIs are attached)

### Publishing a new release

1. Move entries in `CHANGELOG.md` from **Unreleased** into a new version section (Added / Changed / Removed / Fixed / Improved) with today's date
2. Commit and push to `main`
3. Tag and push the tag, e.g. for version 1.0.1:

```batch
git tag v1.0.1
git push origin v1.0.1
```

GitHub Actions then builds all 8 exes and publishes the GitHub Release automatically, using the matching `CHANGELOG.md` section as the release notes.

## Running

Each executable is a standalone Windows application:

- Double-click the `.exe`
- Press `Esc` to close a menu
- Drag the top bar to move the window

## Credits

- **UI source code:** every `.cpp` file in `src/` comes from the [**maotaw-cmd/c-**](https://github.com/maotaw-cmd/c-) repository by [maotaw-cmd](https://github.com/maotaw-cmd). Full credit for the UI designs and their implementation belongs to the original author.
- **This repository** provides the Visual Studio 2022 solution, GitHub Actions build/release automation, and documentation around that code. It claims no authorship or ownership of the original UI code.
- Every source file also carries an attribution header pointing to the original repository.
- If you are the original author and want additional credit, an attribution change, or removal of this code, please open an issue and it will be handled immediately.

## Notes

- These are **UI templates only** — no game/process integration
- All settings are stored in `%APPDATA%` subfolders
