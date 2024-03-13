---- 0000 = clear flags
---- 0001 = load
---- 0010 = store
---- 0011 = mov immediate
---- 0100 = jump register
---- 0101 = jump addres
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
Micro Instructions
1: pc enable, mar set, bus1 enable, acc set 

2: ram enable, inst set

3: acc enable, pc set

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

4: pc enable, mar set, bus1 enable, acc set

5: ram enable, register(b) set

6: acc enable, pc set

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
2 = nonjump location

pc = 0
0: pc enable, mar set, bus1 enable, acc set 

1: ram enable, inst set

2: acc enable, pc set

pc = 1
3: pc enable, mar in				//put 1 in mar 
   b1 on, acc set				//add 1 to pc(1), put 2 in acc

4: acc out, pc in				//put 2 in pc

pc = 2
//if condition true
5: ram out, pc in				//put 2 in mar
						//put address in 2 in pc

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












