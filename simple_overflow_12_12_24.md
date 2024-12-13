https://crackmes.one/crackme/5f05ec3c33c5d42a7c66792b

When loading it into ghidra and taking a look at the login function we can see, that we allocate two blocks of memory.
One with 16 bytes and one with 8 bytes. In typical malloc manner, the blocks are nearby.
The overflow is possible because of the fgets, because the limit is not 16 but 160!

The two blocks are 32 bytes appart, the first 16 byte are from the allocated input buffer, so there are only 16 extra bytes between.
We can now write exactly 31 character, all being 0, to change the value of the static 1.
