https://crackmes.one/crackme/64e91b92d931496abf9091e3

i opend up the executable in ghidra and went straight into the main method.
There is much going on but the interessting part is the hardcoded string, which is copied and the encrypt method.
This string is the string, which we want to have with our input *after* the encryption, because we compare them later on.
The encrypt method is really basic. It just subtracts 10 from each character of the input.
To generate the input, which we need to provide to get the hardcoded string after the encryption, we can just reverse the
encryption function by chaning `+ -10` to `+10`.
We can then pass the static string from the disassembled executable into that reversed function to get the input, which we
need to provide to get back to the hardcoded string after the input is processed in the original encrypt method.

Implementation:
```c
#include <stdio.h>
#include <string.h>

void encrypt(char *block, int flag) {
    size_t len;
    int i;
    while((len = strlen(block)) && len > i) {
        block[i] = block[i] + 10;
        i++;
    }
    return;
}

void generateKey() {
    char a[48] = "9J<q=^\':h*#*d:#+Jh*9)#\'+#>)\'Bs";
    int edflag = (int)*a;
    encrypt(a, edflag);
    printf("%s\n",a);
}

int main() {
    generateKey();
    return 0;
}
```
The password is: CTF{Gh1Dr4-4nD-5Tr4C3-15-H31L}
