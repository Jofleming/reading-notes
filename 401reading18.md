# Cryptography

## Encryption Decryption and Hacking

[Reading](https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:online-data-security/xcae6f4a7ff015e7d:data-encryption-techniques/a/encryption-decryption-and-code-cracking)

Ceaser Cipher was a simple substituion cipher. Specifically the alaphabet was shifted a certain amount of spaces and written like that.

Three main ways someone would try to crack this code are: Frequency Analysis, Known Plaintext, and Brute Force.

### Frequency Analysis

Human languages tend to use some letters more than others. In English that is the letter E. We can analyze the frequency of characters in the message, and identify the most likely E. Narrowing down the possible shift amounts based on that.

### Known Plaintext

If you already knew some part of the plaintext, it is easier to crack the encryption.

Messages tend to start with similar beginnings. In WWII, encrypted German messages always started with a weather forecast, which ultimately made them easier for British mathematician Alan Turing to crack.

### Brute Force

There are only 25 possible shifts (not 26 — why not?). The enemy could take some time to try out each of them and find one that yielded a sensible message. They wouldn't even need to try the shifts on the entire message, just the first word or two.

## Ceasar Cipher

[Reading](https://en.wikipedia.org/wiki/Caesar_cipher)

The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the scheme, A -> 0, B -> 1, ..., Z -> 25.Encryption of a letter x by a shift n can be described mathematically as,

E_{n}(x) = (x+n)    mod 26

Decryption is performed similarly,

D_{n}(x) = (x-n)    mod 26

(There are different definitions for the modulo operation. In the above, the result is in the range 0 to 25; i.e., if x + n or x − n are not in the range 0 to 25, we have to subtract or add 26.)

The replacement remains the same throughout the message, so the cipher is classed as a type of monoalphabetic substitution, as opposed to polyalphabetic substitution.

## Cryptography Crash Course

[Video](https://www.youtube.com/watch?v=jhXCTbFnK8o)

Defense in depth. Many levels of varying security systems.

Use a cipher, turns plain text into nonsense. You need to have key to decrypt.

Use one way functions for key trading.

Key trading allows a cryptographer to give an updated key to a user that is private even through the public net.


[Back](README.md)