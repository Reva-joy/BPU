
`timescale 1ns / 1ps

module tb_branch_prep_tb;

    reg clk;
    reg reset;
    reg branch_valid;
    reg branch_taken_actual;
    reg [7:0] pc;
    wire prediction;

    // Instantiate the predictor
    branch_predictor_2bit uut (
        .clk(clk),
        .reset(reset),
        .branch_valid(branch_valid),
        .branch_taken_actual(branch_taken_actual),
        .pc(pc),
        .prediction(prediction)
    );

    // Clock generation
    initial clk = 0;
    always #5 clk = ~clk;  // 10ns clock period

    initial begin
        $display("Starting 2-bit Branch Predictor Test...");
        $monitor("Time=%0t | PC=%h | Actual=%b | Predicted=%b | Counter=%b",
                 $time, pc, branch_taken_actual, prediction, uut.counter_table[pc]);

        // Initialize
        reset = 1;
        branch_valid = 0;
        branch_taken_actual = 0;
        pc = 8'h00;
        #10;

        reset = 0;

        // Simulate a series of branches at PC = 0x00
        repeat (4) begin
            branch_valid = 1;
            branch_taken_actual = 1;  // Taken
            pc = 8'h00;
            #10;
        end

        repeat (3) begin
            branch_valid = 1;
            branch_taken_actual = 0;  // Not taken
            pc = 8'h00;
            #10;
        end

        // Try a different PC
        branch_valid = 1;
        branch_taken_actual = 1;
        pc = 8'h10;
        #10;

        branch_valid = 1;
        branch_taken_actual = 0;
        pc = 8'h10;
        #10;

        $finish;
    end

endmodule
