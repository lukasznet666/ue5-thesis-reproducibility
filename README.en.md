# Reproducibility package — Unreal Engine 5 thesis

This repository accompanies an engineering thesis on the performance impact of selected Unreal Engine 5 rendering technologies.

Its purpose is to make the **experimental procedure reproducible** and to provide guidance for building functionally equivalent test scenes without publishing the complete Unreal Engine projects, full Blueprint graphs, full program source code, or licensed assets.

The repository documents:
- software/hardware configuration,
- common rendering settings,
- experimental variants,
- scene-reconstruction criteria,
- measurement protocol,
- data-processing method,
- verified reference results.

Exact `CameraActor` coordinates and identical asset packages are not required. Within each comparison, the camera position, orientation and field of view must remain unchanged, while the scene should preserve a functionally similar visible geometry and workload.

Environment 3 used Epic Games' **Valley of the Ancient** demo project, downloaded through Epic Games Launcher and run in Unreal Engine 5.5.4.

Raw CSV Profiler logs are intentionally not included. The package contains the verified reference values used in the thesis and a complete description of the recording and analysis procedure.

See `README.md` for the complete Polish description and `docs/` for technical details.
