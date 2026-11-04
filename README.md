# BattGuard

BattGuard is a KiCad hardware design for a solar-assisted battery charger and power-management board. The project combines a 12 V charging path, protected power inputs, regulated system rails, battery monitoring, and an ESP32-S3 control interface on one board.

The design has progressed from an initial schematic into a nearly complete, routed PCB project. The current revision includes cleaned-up routing, test points, connector and switch footprints, populated protection and filtering components, and a shared component library with symbols, footprints, and 3D models.

## What the board includes

- **Battery charging:** BQ25756-based charger and power-path circuitry, with solar/charge input support and thermistor monitoring.
- **Power conversion:** 5 V buck regulation, 3.3 V regulation, and a boost circuit for the higher-voltage charging rail.
- **Protection:** reverse-polarity and reverse-current protection, transient suppression, input fusing, and protected power switching.
- **Measurement:** INA226 current/voltage monitoring with a dedicated shunt and I²C connectivity.
- **Control and telemetry:** ESP32-S3 header, GPIO breakouts, charge-enable control, status indicators, pushbuttons, and external connectors.
- **Serviceability:** labeled test points, modular connectors, and a board layout prepared for review and fabrication.

## Project status

The schematic and PCB are actively maintained and are at the late-stage design-review/fabrication-preparation phase. Recent work has focused on final trace routing, power-trace sizing, test-point and control-interface placement, silkscreen cleanup, and KiCad DRC cleanup. Fabrication, assembly, bring-up, and electrical validation are still separate steps and should not be inferred from the design files alone.

## Repository layout

```text
board/
├── BattGuard/       # Main schematic, PCB, rules, and project files
├── Datasheets/      # Component datasheets used during design
├── libs/
│   ├── 3dmodels/    # Local STEP models
│   ├── footprints/  # Shared TeamLib footprints
│   └── symbols/     # Shared KiCad symbols
├── fp-lib-table      # Project footprint-library configuration
└── sym-lib-table     # Project symbol-library configuration
```

The main KiCad project is `board/BattGuard/BattGuard.kicad_pro`. Library paths are project-relative, so the shared symbols, footprints, and models travel with the repository and do not require machine-specific absolute paths.

## Opening the project

1. Clone the repository.
2. Open `board/BattGuard/BattGuard.kicad_pro` in KiCad.
3. Confirm that the project loads the committed `TeamLib` symbol and footprint libraries.
4. Review the schematic, PCB, and design rules together before making layout changes.

## Contributing

When adding or changing a component, keep its symbol, footprint, and 3D model in the shared library structure under `board/libs/`. Verify that the part loads correctly in KiCad and that the schematic and PCB remain consistent. Avoid simultaneous edits to the same schematic sheet or PCB layout region, and tag known fabrication snapshots so board revisions remain traceable.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the component-library workflow.

## Team

BattGuard is a Team 23 senior-design project by Brendan Duffy, Jon Mensah, Zachary Sydenstricker, and Tyler Wuthrich.
