# 4-bit-Ripple-Carry-Adder

## Name : Elamaran S E
## Reg No : 212222230036
## Question : 
Simulate verilog HDL for 4 bit Ripple Carry Adder using Quartus II 
## PROGRAM
```
// 1. 1‑bit Full Adder
module full_adder(
    input  wire A,
    input  wire B,
    input  wire Cin,
    output wire Sum,
    output wire Cout
);
    assign Sum  = A ^ B ^ Cin;
    assign Cout = (A & B) | (Cin & (A ^ B));
endmodule

// 2. 4‑bit Ripple Carry Adder
module ripple_carry_adder_4bit(
    input  wire [3:0] A,
    input  wire [3:0] B,
    input  wire       Cin,
    output wire [3:0] Sum,
    output wire       Cout
);
    wire C1, C2, C3;

    full_adder fa0 (.A(A[0]), .B(B[0]), .Cin(Cin), .   Sum(Sum[0]), .Cout(C1));
    full_adder fa1 (.A(A[1]), .B(B[1]), .Cin(C1),  .   Sum(Sum[1]), .Cout(C2));
    full_adder fa2 (.A(A[2]), .B(B[2]), .Cin(C2),  .   Sum(Sum[2]), .Cout(C3));
    full_adder fa3 (.A(A[3]), .B(B[3]), .Cin(C3),  .   Sum(Sum[3]), .Cout(Cout));
endmodule

// 3. Top‑level module named "workshop"
module workshop(
    input  wire [3:0] A,    // connect these to your FPGA pins
    input  wire [3:0] B,
    input  wire       Cin,
    output wire [3:0] Sum,
    output wire       Cout
);
    // instantiate the 4‑bit ripple carry adder
    ripple_carry_adder_4bit UUT (
        .A   (A),
        .B   (B),
        .Cin (Cin),
        .Sum (Sum),
        .Cout(Cout)
    );
endmodule
```

## OUTPUT

![image](https://github.com/user-attachments/assets/2b072638-d181-4c6d-bb3a-1fce38a9aa65)



