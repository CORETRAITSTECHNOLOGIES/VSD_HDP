# Lab 8: Ternary muxes, blocking caveat and gate-level simulation

**Screenshots supplied:** 10. Original filenames and individually ordered image embeds are provided in the complete prepared archive.

## Lab focus

Ternary muxes, blocking caveat and gate-level simulation — synthesis, RTL simulation, or cell-mapping evidence as indicated by the uploaded screenshot names.

## Command evidence

Examples recorded in the supplied terminal history (not necessarily one uninterrupted successful sequence):

```console
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux
write_verilog -noattr ternary_operator_mux_net.v
```

## Evidence and limitations

These notes were organized from the uploaded **Week_2.zip** screenshots and terminal histories. They describe the observed workflow; they do not invent missing Verilog source files or claim to reproduce unprovided simulations.

The complete **75 PNG files and five original text log files** are preserved in the prepared Week2 archive provided in chat. **Binary screenshots are not yet committed to GitHub**. After uploading that archive's Week2 folder, the corresponding images will appear under each lab's `images/` directory.
