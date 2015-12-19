# single-cycle-implementation

module counter (clk, R, Control, ALU, PC, Branch);

  input wire clk, R, Control, Branch, Alu;
  output reg PC;
  
  always @(posedge clk or posedge R)
  begin
    if (ALU == 0)
    begin
      case (control)
        "branch code" : PC <= PC + 4 + {{14(Branch[15])}, Branch[15:0], 2b'00};
        default ALU <= PC + 4;
      end case
    end
  end
end module
