https://crackmes.one/crackme/6640d1d26b8bd8ddfe33c80a

We can open the executable in ghidra and go through the disassembled C-Code.
We see that in main we read in the password from the user and check in in the check() method.
In the check method we get the length of our input and check if:
- if the length is 10
- the first char is 1
- the 5. char is 9
we can create a simple password, that fullfills these requirements like: 1999999999
