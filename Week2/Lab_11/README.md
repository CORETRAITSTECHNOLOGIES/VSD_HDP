# Lab 11: Generated mux/demux, case demux and ripple-carry adder

**Screenshots supplied:** 9. Original filenames and individually ordered image embeds are provided in the complete prepared archive.

## Lab focus

Generated mux/demux, case demux and ripple-carry adder — synthesis, RTL simulation, or cell-mapping evidence as indicated by the uploaded screenshot names.

## Command evidence

Examples recorded in the supplied terminal history (not necessarily one uninterrupted successful sequence):

```console
iverilog mux_generate.v tb_mux_generate.v
./a.out
gtkwave tb_mux_generate.vcd
read_verilog mux_generate.v
synth -top mux_generate
write_verilog -noattr mux_generate_net.v
```

## Evidence and limitations

These notes were organized from the uploaded **Week_2.zip** screenshots and terminal histories. They describe the observed workflow; they do not invent missing Verilog source files or claim to reproduce unprovided simulations.

The complete **75 PNG files and five original text log files** are preserved in the prepared Week2 archive provided in chat. **Binary screenshots are not yet committed to GitHub**. After uploading that archive's Week2 folder, the corresponding images will appear under each lab's `images/` directory.
