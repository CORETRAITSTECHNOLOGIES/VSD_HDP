# Lab 7: Unused outputs and counter optimization

**Screenshots supplied:** 2. Original filenames and individually ordered image embeds are provided in the complete prepared archive.

## Lab focus

Unused outputs and counter optimization — synthesis, RTL simulation, or cell-mapping evidence as indicated by the uploaded screenshot names.

## Command evidence

Examples recorded in the supplied terminal history (not necessarily one uninterrupted successful sequence):

```console
read_verilog counter_opt.v
synth -top counter_opt
read_verilog counter_opt2.v
synth -top counter_opt2
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

## Evidence and limitations

These notes were organized from the uploaded **Week_2.zip** screenshots and terminal histories. They describe the observed workflow; they do not invent missing Verilog source files or claim to reproduce unprovided simulations.

The complete **75 PNG files and five original text log files** are preserved in the prepared Week2 archive provided in chat. **Binary screenshots are not yet committed to GitHub**. After uploading that archive's Week2 folder, the corresponding images will appear under each lab's `images/` directory.
