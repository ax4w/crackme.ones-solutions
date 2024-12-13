https://crackmes.one/crackme/61c8deff33c5d413767ca0ea

i disassembled the executable using ghidra and reimplemented the key generation algorithm and all needed data:
```c
  local_c3[0] = 0x34;
  local_c3[1] = 0x40;
  local_c3[2] = 0x73;
  local_c3[3] = 0x73;
  local_c3[4] = 0x37;
  local_c3[5] = 0x32;
  local_c3[6] = 0x34;
  local_c3[7] = 0x35;
  local_c3[8] = 0x33;
  local_c3[9] = 0x36;
  local_c3[10] = 0;
  ...
  local_cc = 0;
  for (i = 0; i < (int)len; i = i + 1) {
    sprintf(local_78 + local_cc,"%02x",(ulong)local_c3[i]);
    local_cc = local_cc + 2;
  }
```
it basiaclly takes the entries of s and converts to a char* and adds them to the key at the offset cc.
the loop could totally be avoided if one would just translate the hex numbers.

an interessting observation is, that the input is stored directly after the entries, which generate the key.

i used that c-code to generate the key:

```c
#include <stdio.h>
#include <string.h>

void generateKey() {
    char s[75] = {0x34,0x40,0x73,0x73,0x37,0x32,0x34,0x35,0x33,0x36,0};
    char key[104];
    size_t len = strlen((char*)s);
    size_t cc = 0;
    for(int i = 0; i < len; i++) {
        sprintf(key+cc,"%02x", s[i]);
        cc += 2;
    }
    printf("%s",key);
}

int main() {
    generateKey();
    return 0;
}
```
key is: 34407373373234353336
