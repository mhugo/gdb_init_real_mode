# gdb_init_real_mode
GDB macros for real mode debugging

If you have to debug ASM code in the good old "real" mode of x86 (with QEMU for instance), you may find this set of macros interesting.

Refer to [this blog post](http://ternet.fr/?p=gdb_real_mode) for some explanations.

Example output of a gdb session:

<pre>
---------------------------[ STACK ]---
0000 0000 0000 0000 0000 0000 0000 0000 
0000 0000 0000 0000 0000 0000 0000 0000 
---------------------------[ DS:SI ]---
00000000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
---------------------------[ ES:DI ]---
00000000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
----------------------------[ CPU ]----
AX: 0000 BX: 0000 CX: 0000 DX: 0633
SI: 0000 DI: 0000 SP: 0000 BP: 0000
CS: F000 DS: 0000 ES: 0000 SS: 0000

IP: C41F EIP:0000C41F
CS:IP: F000:C41F (0xFC41F)
SS:SP: 0000:0000 (0x00000)
SS:BP: 0000:0000 (0x00000)
OF <0>  DF <0>  IF <0>  TF <0>  SF <0>  ZF <0>  AF <0>  PF <0>  CF <0>
ID <0>  VIP <0> VIF <0> AC <0>  VM <0>  RF <0>  NT <0>  IOPL <0>
---------------------------[ CODE ]----
   0xfc41f:	mov    eax,cr0
   0xfc422:	and    eax,0x9fffffff
   0xfc428:	mov    cr0,eax
   0xfc42b:	cli    
   0xfc42c:	cld     
   0xfc42d:	mov    eax,0x8f
   0xfc433:	out    0x70,al
   0xfc435:	in     al,0x71
   0xfc437:	cmp    al,0x0
   0xfc439:	jne    0xfc44e
   
</pre>
