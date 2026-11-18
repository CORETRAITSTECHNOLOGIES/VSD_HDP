# VSD Hardware Design Program — Week 2

## RTL Design and Synthesis Workshop

This week covers the uploaded evidence from 11 labs and a 55-lecture training sequence reported as completed.

**Source archive:** 75 screenshots (PNG) and 5 text log files. Some images are named with minor typos; the complete prepared archive preserves the filenames as uploaded. The provided ZIP contained no actual Verilog source or VCD files.

| Lab | Topics | Screenshots |
|---|---|---:|
| [Lab 1](Lab_01/README.md) | Introduction and RTL synthesis workflow | 1 |
| [Lab 2](Lab_02/README.md) | Design instantiation and GTKWave | 3 |
| [Lab 3](Lab_03/README.md) | Yosys synthesis, ABC mapping and netlists | 8 |
| [Lab 4](Lab_04/README.md) | Hierarchical versus flattened synthesis | 7 |
| [Lab 5](Lab_05/README.md) | Flip-flops, reset and multiplication optimization | 10 |
| [Lab 6](Lab_06/README.md) | Constant propagation and sequential optimization | 12 |
| [Lab 7](Lab_07/README.md) | Unused outputs and counter optimization | 2 |
| [Lab 8](Lab_08/README.md) | Ternary muxes, blocking caveat and gate-level simulation | 10 |
| [Lab 9](Lab_09/README.md) | Incomplete if statements and inferred latches | 4 |
| [Lab 10](Lab_10/README.md) | Case statements and case inference | 9 |
| [Lab 11](Lab_11/README.md) | Generated mux/demux and ripple-carry adder | 9 |

## Common workflow

```bash
iverilog design.v tb_design.v
./a.out
gtkwave tb_design.vcd
yosys
```

Within Yosys:

```tcl
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog design.v
synth -top design
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr design_net.v
```

These are generalized forms of the logged commands. Not all steps were used in every lab. Some terminal attempts in the logs contain errors or typos and should not be treated as successful runs.

## Image and log upload status

Lab README files are committed to GitHub. The **original images and logs have been arranged in a downloadable ZIP** and must still be uploaded as files to the repository; they are not yet present on GitHub. The full archive's per-lab READMEs include **individual inline image embeds**, each beside a caption and ordered by lab. Extract it and use `git add Week2 && git commit -m "Add Week 2 screenshots and logs" && git push origin main` in your cloned repository.

## Provenance

Lab names were inferred from uploaded screenshots and available terminal transcripts. Lectures 1–55 themselves were not provided. No RTL, VCD or tests were recreated.
