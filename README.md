🧠 Branch Prediction Unit (BPU) — Verilog HDL

This project implements a dynamic 2-bit branch prediction unit to reduce control hazards in a pipelined processor.
It uses a Pattern History Table (PHT) of 2-bit saturating counters to predict whether a branch will be taken or not, improving CPU performance.

🔧 Features

Dynamic 2-bit predictor (Saturating counter)

Pattern History Table (PHT)-based prediction

Fully synthesizable and FPGA-tested design (Intel MAX V)

Verilog HDL implementation with ModelSim simulation

🧩 Methodology

Instruction fetch and branch identification

PHT lookup for prediction

Counter update after actual branch outcome

Prediction accuracy improves with each iteration

💻 Tools Used

Intel Quartus Prime – Design synthesis

ModelSim – Functional simulation


📈 Output Waveform Explanation

In the ModelSim simulation:

clk – system clock signal.

branch_taken – actual outcome of the branch (1 = taken, 0 = not taken).

predict_taken – predictor’s output (1 = predicted taken, 0 = not taken).

state – 2-bit saturating counter value (00, 01 = predict not taken; 10, 11 = predict taken).

Interpretation:

Initially, the predictor may mispredict (e.g., predicts not-taken when taken).

With repeated branch outcomes, the counter saturates toward the correct prediction (11 or 00).

The waveform shows predictor adaptation — mispredictions early, then stable correct predictions as it “learns” the branch behavior.
