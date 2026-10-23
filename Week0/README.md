# Week 0 — VSD Hardware Design Program: EDA Environment Verification

**Date:** 23 October 2026  
**Environment:** Tiny Tapeout Analog Ubuntu VM running in Oracle VirtualBox  
**Goal:** Check the VSD open-source EDA toolchain and validate a sample RTL-to-GDSII flow.

## Tools verified

| Tool | Role | Observed result | Status |
| --- | --- | --- | --- |
| Yosys | RTL synthesis | `Yosys 0.9 (git sha1 1979e0b)` | Launched |
| Icarus Verilog | Verilog compilation/simulation | `iverilog` printed usage; no source supplied | Installed; functional test pending |
| GTKWave | Simulation waveform viewer | GUI launched; version `3.3.104` | Launched |
| OpenSTA | Static timing analysis | `OpenSTA 2.0.17` prompt opened | Launched |
| ngspice | SPICE circuit simulation | `ngspice-44` prompt opened | Launched |
| Magic | Physical IC layout | Layout editor opened, technology shown as `minimum` | Launched; SKY130 setup not independently checked |
| Docker | OpenLane container runtime | `Docker version 28.3.3` | CLI available |
| OpenLane | RTL-to-GDSII automation | `make test` completed for the `spm` example | **Passed** |

**Note:** Running `openlane` directly displayed `command not found`. The legacy OpenLane flow is invoked using its Makefile / `flow.tcl`; the successful integration test establishes that OpenLane was usable in this VM.

## Commands used

```bash
yosys
iverilog
gtkwave
sta
ngspice
magic
docker --version
```

Interactive sessions (such as `yosys`, `sta`, and `ngspice`) can be exited using their application-specific exit commands. Launching tools verifies availability, **not** correctness on a complete user design.

### OpenLane integration test

The supplied OpenLane setup was tested with the `spm` reference design. The final terminal output included:

```text
[INFO]: There are no max slew, max fanout or max capacitance violations in the design at the Typical corner.
[INFO]: There are no hold violations in the design at the Typical corner.
[INFO]: There are no setup violations in the design at the Typical corner.
[SUCCESS]: Flow complete.
Basic test passed
```

Additional results visible in the log:

- Detailed routing completed.
- Magic DRC reported no violations after GDS export.
- KLayout DRC reported no violations after GDS export.
- The KLayout/Magic XOR comparison reported no differences.
- LVS, parasitic extraction, and multi-corner STA stages ran.
- Final manufacturability and metrics reports were generated.

**Warning:** `VSRC_LOC_FILES` was not set, so the IR-drop report can be inaccurate. The tool noted this may be ignored for a design not integrated into a top-level chip. This warning did **not** prevent the sample flow from passing.

### Key output location

The run logs showed a sample run path similar to:

```text
designs/spm/runs/openlane_test/
├── logs/
├── reports/
└── results/
    └── final/
```

Depending on how the container is mounted, these paths may be relative to the OpenLane work directory.

## Lessons learned

The tools correspond to different abstraction levels of chip design:

```text
Verilog RTL
  ├── Icarus Verilog + GTKWave: functional simulation and waveforms
  └── Yosys: synthesis
            ↓
       Gate-level netlist
            ├── OpenSTA: timing analysis
            └── OpenLane: physical implementation → GDSII
                         └── Magic: layout inspection / DRC

ngspice: electrical/transistor-level circuit simulation
```

The Tiny Tapeout VM already included a usable EDA setup; the legacy OpenLane sample was able to complete end-to-end.

## Pending hands-on validation

- [ ] Write and simulate a small Verilog module plus testbench with `iverilog` and `vvp`.
- [ ] Generate a `.vcd` file and inspect it in GTKWave.
- [ ] Synthesize the design in Yosys and examine the netlist.
- [ ] Verify the SKY130 technology setup for Magic.
- [ ] Explore the OpenLane `spm` synthesis, timing and physical-design reports.
- [ ] Add screenshots of the terminal and tool GUIs to this directory.

## Screenshot evidence

Nine screenshots of the tool startup checks and the successful OpenLane test were captured. They are kept in the accompanying local Week 0 GitHub package; they are not embedded here until the image files have been committed into this repository.

## References

- [VSD Hardware Design Program](https://www.vlsisystemdesign.com/)
- [Yosys](https://github.com/YosysHQ/yosys)
- [Icarus Verilog](https://github.com/steveicarus/iverilog)
- [GTKWave](https://gtkwave.sourceforge.net/)
- [OpenSTA](https://github.com/parallaxsw/OpenSTA)
- [ngspice](https://ngspice.sourceforge.io/)
- [Magic](https://github.com/RTimothyEdwards/magic)
- [Legacy OpenLane](https://github.com/The-OpenROAD-Project/OpenLane)

> Legacy OpenLane is now in maintenance mode; for new independent designs, see its successor [LibreLane](https://github.com/librelane/librelane). This VSD exercise retains the course-compatible OpenLane workflow.
