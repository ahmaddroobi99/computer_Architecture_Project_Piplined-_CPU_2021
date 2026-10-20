# Pipelined MIPS CPU in Verilog

Computer-architecture course project: a **pipelined MIPS datapath** in Verilog.

Includes ALU and ALU control, register file, instruction/data memories, sign/zero extend, muxes, forwarding unit, stall control, flush, JR control, and a testbench (`MIPSStimulus.v`). Instruction stream: `Project_arch/instr.txt`. Notes: `Project_arch/multi_cycle.pdf`.

This is a student CPU, not an FPGA product.

**Stack:** Verilog

## How to run

Top-level testbench: `MIPSStimulus` (clock and reset only, no `$finish`, so stop the simulation yourself). `InstructionMem.v` loads `instr.txt` with a relative path, so run the simulator from `Project_arch/`.

The original simulator isn't recorded here. Icarus Verilog 12 rejects `StallControl.v` as written: `EX_rt`, `ID_rs` and `ID_rt` are declared as scalar inputs and then as `wire [4:0]`. With that declaration changed to `input [4:0]` in a local copy, the rest compiles and simulates under Icarus with:

```bash
cd Project_arch
iverilog -s MIPSStimulus -o cpu.vvp *.v
vvp cpu.vvp
```

---
Historical **BSc Computer Engineering** work (An-Najah National University, 2021). Kept for provenance — not current research.

Current work: [github.com/ahmaddroobi99](https://github.com/ahmaddroobi99)
