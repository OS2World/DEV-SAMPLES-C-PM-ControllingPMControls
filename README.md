# DEV-SAMPLES-C-PM-ControllingPMControls

## Description

This sample demonstrates how to implement a custom PM control by **superclassing** an existing PM window class. The `BAR` control is built on top of `WC_STATIC` and renders a decorative horizontal or vertical separator bar — with optional text, raised/depressed appearance, mnemonic support, and auto-sizing.

The project was originally written by Alessandro Cantatore in 2002 for IBM VisualAge C++ on OS/2.

Article: http://www.edm2.com/index.php/Controlling_PM_Controls

## What it demonstrates

- **Superclassing**: registering a new window class (`WC_BAR`) that intercepts messages before forwarding to the original `WC_STATIC` window procedure
- **Custom control styles**: `BARS_VERTICAL`, `BARS_RAISED`, `BARS_THICK`, `BARS_AUTOSIZE`, `BARS_CENTER`, `BARS_RIGHT`, `BARS_MNEMONIC`
- **Presentation parameters**: responding to font/color changes via `WM_PRESPARAMCHANGED`
- **Window parameters protocol**: implementing `WM_SETWINDOWPARAMS` / `WM_QUERYWINDOWPARAMS` for text and control-data queries
- **Mnemonic support**: `WM_MATCHMNEMONIC` handling and underline drawing
- **3D border rendering**: `Win3DBorderDraw()` utility in `ctrlutil.C`
- **Control text measurement**: `CtrlTextSet()` / `CtrlTextSize()` / `CtrlTextDraw()` helpers

## Files

```
src/
  ctrlutil.C      - PM control utility functions (text, color, border drawing)
  superclass.C    - Bar control registration, window proc, paint, and main()
  ctrlutil.h      - CTRLTXT, SIZES structures and ctrlutil function prototypes
  superclass.h    - WC_BAR class name, BARS_* style constants, BARM_* messages
  dllmain.h       - Common includes, memory allocation macros (BUILD_TEST_EXE)
  ApiExPM.h       - General PM macros (MRFALSE, MRTRUE, RectSet, WinStyle, ...)
  bar.rc          - Dialog resource with nine BAR control instances
  bar-gcc.def     - Module definition file for GCC/wlink build
  bar-ow.lnk      - Linker response file for OpenWatcom wlink
```

## Build

### GCC 9.2 / kLIBC (bitwiseworks)

```
compile-gcc.cmd
```

Output: `bin-gcc\BAR.EXE`

### OpenWatcom 2.0

```
compile-ow.cmd
```

Output: `bin-ow\BAR.EXE`

## Running

Execute `BAR.EXE` on OS/2 (ArcaOS 5.0.7 or later recommended). A dialog window appears showing nine bar controls demonstrating all style combinations.

## History

- **2002-01-10** — Alessandro Cantatore — Original version 0.1, built with IBM VisualAge C++
- **2026-07-28** — Martin Iturbide — Moved sources to `src/`, added GCC and OpenWatcom build systems, fixed `main()` return type

## License

BSD 3-Clause

## Authors

- Alessandro Cantatore
- Martin Iturbide
