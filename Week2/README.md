# VSD Hardware Design Program — Week 2

> RTL design, logic synthesis, simulation and synthesis optimization workshop evidence.

## Scope and provenance

This folder organizes **75 uploaded PNG screenshots** into Labs **1–11** and retains the supplied text logs. The uploaded archive did **not** contain Verilog source files or standalone VCD files. The images are presented individually in their corresponding lab READMEs. Lab topics are derived from original filenames and log content, not asserted to be official lecture titles.

| Lab | Topic | Images |
|---|---|---:|
| [Lab 01](Lab_01/README.md) | Introduction and RTL synthesis workflow | 1 |
| [Lab 02](Lab_02/README.md) | Design instantiation and GTKWave | 3 |
| [Lab 03](Lab_03/README.md) | Yosys synthesis, ABC mapping and netlists | 8 |
| [Lab 04](Lab_04/README.md) | Hierarchical versus flattened synthesis | 7 |
| [Lab 05](Lab_05/README.md) | Flip-flops, asynchronous/synchronous reset and multiplication optimization | 10 |
| [Lab 06](Lab_06/README.md) | Constant propagation and sequential optimization | 12 |
| [Lab 07](Lab_07/README.md) | Unused outputs and counter optimization | 2 |
| [Lab 08](Lab_08/README.md) | Ternary muxes, blocking caveat and gate-level simulation | 10 |
| [Lab 09](Lab_09/README.md) | Incomplete if statements and inferred latches | 4 |
| [Lab 10](Lab_10/README.md) | Case statements: complete, incomplete, partial and bad cases | 9 |
| [Lab 11](Lab_11/README.md) | Generated mux/demux, case demux and ripple-carry adder | 9 |

## Recorded toolchain and command patterns

The following commands (or close variants) appear in the terminal logs. Run them from the workshop `verilog_files` directory with the relevant input files available.

```bash
# RTL simulation
iverilog design.v tb_design.v
./a.out
gtkwave tb_design.vcd

# Launch Yosys
yosys
```

Typical commands inside Yosys, assembled from recorded examples:

```tcl
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog design.v
synth -top design
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr design_net.v
```

For gate-level simulation the Lab 8 and Lab 10/11 logs also show compiling the mapped netlist with Sky130 `primitives.v` and `sky130_fd_sc_hd.v` library models plus a testbench. These generalized examples are **not** intended as a verbatim script that was run in every lab.

## Logs

Original log sources are copied to related labs. `New Text Document.txt` duplicates `Logs_lab4_pt1.txt` and is not repeated in each lab; the unchanged extra copy is preserved in `source_archive/`.

## Important limitations

- The ZIP proves 75 screenshots and terminal output, **not** individual completion of all 55 lectures.
- Lab 1–3, 5, and 9 did not include individually matched terminal histories; screenshots are the evidence there.
- All image names are preserved exactly for traceability.
- Screenshots can show specific tool outputs, but original RTL is not present to reproduce these results independently.
