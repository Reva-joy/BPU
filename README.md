# BPU
Overview
This project implements a Branch Prediction Unit (BPU) for a pipelined processor in Verilog HDL. The design utilizes a dynamic, 2-bit saturating counter-based predictor, maintaining a Pattern History Table (PHT) to improve CPU throughput by minimizing control hazards caused by conditional branch instructions.

Features
2-bit dynamic predictor (saturating counters) for each indexed branch instruction

Pipelined and synthesizable design ready for FPGA deployment (tested on Intel MAX V family, Quartus Prime 17.1)

RTL simulations provided (ModelSim) with real branch scenarios

Modularized code and testbenches, suitable for integration in larger CPU projects

Prerequisites
Quartus Prime (tested with Lite/Standard Edition 17.1+)

ModelSim (for functional simulation)

Verilog HDL support


Open the Quartus project and add source files from src/.

Run simulation in ModelSim with demo1_tb.v to observe prediction behavior.

Compile and synthesize for your FPGA device (edit parameters for your target board).

Example
To simulate:

Load file.v and file_tb.v in ModelSim.

Run simulation and check waveform outputs for prediction cycles and counter updates.


git clone https://github.com/your-username/branch-prediction-unit.git
Add src/ files to a Quartus project.

Run the testbench in ModelSim (tb/demo1_tb.v) to see prediction behavior.

Synthesize the design for your FPGA; optimize PHT size for your device.
