https://crackmes.one/crackme/659fde9deef082e477ff59ba

we can look into the code and inspect how check_all works.
check_all calls check_len of our input,where we return true if the input.length % 4 == 0
so we know that we need a by 4 divisble password. the second function is check_palindrome_every_four
which is called on our input two time. first to check if [0:3] is a palindrome and if [4:7] is a palindrome.
we now know that the password needs to be 2 palindromes with a length of 8. so 11111111 is a valid solution, since
its 8 chars long and is made of two palindromes with the length 4.