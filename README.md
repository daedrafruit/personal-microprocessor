**Custom Microprocessor made in [Digital](https://github.com/hneemann/Digital)**  
Found in programs folder are some simples tests (some WIP).  
I used [Customasm](https://github.com/hlorenzi/customasm) to make the programming process much less of a headache.   
_______________________________________  
**Instructions**
_______________________________________  

---- 0000 = clear flags  
---- 0001 = load  
---- 0010 = store  
---- 0011 = mov immediate  
---- 0100 = jump register  
---- 0101 = jump address  
---- 0110 = jump conditional  
---- 0111 = nop  
  
---- 1000 = ADD  
---- 1001 = CMP  
---- 1010 = SHL  
---- 1011 = SHR  
---- 1100 = NOT  
---- 1101 = AND  
---- 1110 = OR  
---- 1111 = XOR  

_______________________________________  
**Clock Cycles**
_______________________________________  
Micro Instructions  
0: pc enable, mar set, bus1 enable, acc set   
  
1: ram enable, inst set  
  
2: acc enable, pc set  
_______________________________________  
ALU  
  
3: register(a)(swap) enable, tmp set  
  
4: register(b) enable, acc set, flag set  
  
5: acc out, register(b) in  
_______________________________________  
Load b from address a  
  
3: register(a)(swap) out, register(b) in,  
  
_______________________________________  
Store b into address a  
  
3: register(a)(swap) out, mar in  
  
4: register(b) out, ram in  
_______________________________________  
Move value from next instruction into b  
  
3: pc enable, mar set, bus1 enable, acc set  
  
4: ram enable, register(b) set  
  
5: acc enable, pc set  
_______________________________________  
Jump to location in b  
  
3: register(b) out, pc set  
_______________________________________  
Jump to address in next instruction  
  
3: pc enable, bus1 enable, acc set  
  
4: acc enable, pc set  
_______________________________________  
Jump Conditional  
  
0 = instruction  
1 = address  
2 = non-jump location  
  
pc = 0  
0: pc enable, mar set, bus1 enable, acc set   
  
1: ram enable, inst set  
  
2: acc enable, pc set  
  
pc = 1  
3: pc enable, mar in  
   b1 on, acc set  
  
4: acc out, pc in  
  
pc = 2  
//if condition true  
5: ram out, pc in  
  
//otherwise  
//2 is in pc and the program can continue  
_______________________________________  
Clear Flags  
  
3: b1 on, alu op out, flg set  
_______________________________________  
IO  
  
s e da io  
  
4: reg enable, io  
  
5 reg enable, io  
