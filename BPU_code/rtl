
// 2-bit Branch Predictor RTL
module branch_prep (
    input clk,
    input reset,
    input branch_valid,           // Indicates if current instruction is a branch
    input branch_taken_actual,    // Actual outcome of the branch
    input [7:0] pc,               // Program Counter (used as index)
    output reg prediction         // Predicted outcome: 1 = taken, 0 = not taken
);

    // 2-bit saturating counters for each PC index
    reg [1:0] counter_table [255:0];  // 256-entry table

    // Prediction logic: MSB of counter determines prediction
    always @(*) begin
        prediction = counter_table[pc][1];  // 2'b10 or 2'b11 = predict taken
    end

    // Counter update logic
    integer i;
    always @(posedge clk or posedge reset) begin
        if (reset) begin
            for (i = 0; i < 256; i = i + 1)
                counter_table[i] <= 2'b01;  // Weakly not taken
        end else if (branch_valid) begin
            case (counter_table[pc])
                2'b00: counter_table[pc] <= branch_taken_actual ? 2'b01 : 2'b00;
                2'b01: counter_table[pc] <= branch_taken_actual ? 2'b10 : 2'b00;
                2'b10: counter_table[pc] <= branch_taken_actual ? 2'b11 : 2'b01;
                2'b11: counter_table[pc] <= branch_taken_actual ? 2'b11 : 2'b10;
            endcase
        end
    end

endmodule




