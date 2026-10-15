# C++ Direct2D UI Collection

A collection of 8 different Direct2D menu UIs for Windows, all built with C++17 and the Win32 API. Each UI is a standalone `.cpp` file that can be compiled individually.

## Requirements

- Windows 10/11
- Visual Studio 2022 (or Build Tools) with MSVC
- Windows SDK
- Direct2D / DirectWrite (included with Windows SDK)

## Project Files

| File | Description |
|------|-------------|
| `KellUI.cpp` | Dark transparent full-width Direct2D menu with Aimbot/Visuals controls, color picker, config system |
| `MaotawTerminal.cpp` | Custom teal terminal with built-in editor, syntax highlighting, context menu, tray integration |
| `MenuSense_Rainbow.cpp` | MenuSense-style UI with animated rainbow top bar, sidebar navigation, config profiles |
| `inabooUI.cpp` | Transparent black menu with connected particles, color picker, config manager |
| `maotaw_ui.cpp` | Screenshot-style ragebot UI with collapsible sidebar, breadcrumb navigation |
| `phantom_ui.cpp` | Purple neon reference UI with animated background, skeleton preview, config system |
| `playhookUI.cpp` | Compact purple UI with hotkey combos (Ctrl+Alt+Shift), RGB color picker, ESP colors |
| `spectraUI.cpp` | Spectra UI with blur effects, companion windows, watermark overlay, keybind/spectator lists |

## Building with VS Code

1. Open this folder in VS Code
2. Make sure you have the **C/C++ extension** installed
3. Open the **Command Palette** (`Ctrl+Shift+P`) → **Tasks: Run Task**
4. Select the UI you want to build (e.g., "Build KellUI")
5. The executable will be created in the `build/` folder

## Building with Visual Studio

1. Open Developer Command Prompt for VS 2022
2. Navigate to this folder
3. Run the build command for the desired UI:

```batch
cl /std:c++17 /EHsc /DUNICODE /D_UNICODE /Febui\ui.exe ui.cpp /link /SUBSYSTEM:WINDOWS d2d1.lib dwrite.lib
```

## Running

Each executable is a standalone Windows application:
- Double-click the `.exe` in the `build/` folder
- Or use VS Code's **Run and Debug** (`F5`) with the appropriate configuration

## Key Features

- **All UIs**: Direct2D rendering, mouse interaction, keyboard input
- **Config system**: Save/Load/Delete configuration profiles
- **Color picker**: HSV-based color selection
- **Hotkey capture**: Click a keybind field and press any key
- **Animated backgrounds**: Particles, gradients, rainbow effects

## Notes

- These are **UI templates only** — no game/process integration
- All settings are stored in `%APPDATA%` subfolders
- Press `Esc` to close any menu
- Drag the top bar to move the window
