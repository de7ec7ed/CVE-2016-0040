CVE-2016-0040
This exploit builds upon SMMRootkit's 32Bit project (https://github.com/Rootkitsmm/cve-2016-0040) which causes this vulnerability to trigger a BSoD with all 'a's in RCX and 'B's in RAX.
It was ported to 64Bit Windows 7 SP1 and doesn't use the "mov [rcx+06h], rax" instruction for inital stage exploitation but instead the "mov [rdx+8h], rdx instruction to place a self-referencing pointer into a bitmap's pvScan0 variable".
In order to cleanup from side-effect corruptions the win32k heap 4096 bitmaps were allocated which made the addresses of corruption in the target bitmap predictable so they could be restored. In order to build read/write
primitives Core Security's, "Abusing GDI for Ring0 Exploit Primities" (https://www.coresecurity.com/blog/abusing-gdi-for-ring0-exploit-primitives) was referenced but build out Manager and Worker
bitmaps that could be used to perform system process token stealing.