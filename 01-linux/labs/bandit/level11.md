# Level 11-12: The password is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Password
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
## Method
Use the 'tr' command emulate ROT13 decryption
```
cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M' 
```

**What I learned:** 'a-zA-Z' is SET1 which are the characters to translate from, 'n-za-mN-ZA-M' is SET2 which are the characters to translate. The ROT13 cipher maps 'a' to 'n', 'b' is mapped to 'o' and so on, this is why SET2 starts with 'n' and goes to 'z' then back around to 'a-m' to complete the second half of the alphabet.