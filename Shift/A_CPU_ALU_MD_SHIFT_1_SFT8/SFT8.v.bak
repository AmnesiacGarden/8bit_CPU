module SFT8 (CLK, M, C0, S, D, QB, CN);
  input CLK, M, C0; 
  input[1:0] S; 
  input[7:0] D;
  
  output[7:0] QB; 
  output CN;
  
  wire[7:0] QB;  
  wire[2:0] ABC;
  wire CN;
  
  reg[7:0] REG; 
  reg CY;
 
always @(posedge CLK)
  
  case (ABC)
  3'b011 : begin REG[0]<=C0; REG[7:1]<=REG[6:0];
           CY<=REG[7]; end
  3'b010 : begin REG[0]<=REG[7]; REG[7:1]<=REG[6:0]; end
  3'b100 : begin REG[7]<=REG[0]; REG[6:0]<=REG[7:1]; end
  3'b101 : begin REG[7]<=C0; REG[6:0]<=REG[7:1]; CY<=REG[0]; end
  3'b110 : begin REG[7:0]<=D[7:0]; end
  3'b111 : begin REG[7:0]<=D[7:0]; end
 
  default : begin REG <= REG ; CY<=CY;end
  endcase

  assign ABC={M,S};  
  assign CN=CY; 
  assign QB[7:0]=REG[7:0];

  endmodule      