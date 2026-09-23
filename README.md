# BattGuard

This repository keeps the KiCad PCB project and the shared component library together. Any symbol, footprint, or 3D model committed by one teammate is available to everyone else after their next pull.

## Team setup

1. Clone this repository.
2. In KiCad, create a new project at `board/` named `board` (this generates `board/board.kicad_pro`, `board/board.kicad_sch`, and `board/board.kicad_pcb`).
3. Re-open `board/board.kicad_pro` from your clone root.
4. In KiCad, check **Preferences > Manage Symbol Libraries** and **Preferences > Manage Footprint Libraries** and confirm `TeamLib` appears with `${KIPRJMOD}`-based paths.

No manual path entry is needed because `sym-lib-table` and `fp-lib-table` are committed in `board/`.

## Collaboration notes

- Avoid simultaneous edits to the same schematic sheet or the same PCB layout region to reduce merge conflicts.
- Tag commits before sending board revisions to fabrication so manufacturing snapshots are easy to trace.
