# Crypto

## Hashing

### Checks

#### Non-Cryptographic Hash

crc32

## Types

### crc32&#x20;

crc32 is a Non-Cryptographic Hashing Algorithm

* Ex: Found 891568578 to equal abc
* Need to convert the integer to Hex followed by 8 zeros. Ex: with unknown admin password
  * `python hex(-432570933 % (1<<32))`
    * '0xe6377dcb'&#x20;
      * `echo "e6377dcb:00000000" > hash.txt`
  * `hashcat -a 0 -m 11500 hash.txt -r rules/oneruletorule.rule rockyou.txt`
    * oqllo7 is the outputted password

### XorShift128+

#### Cracking

[https://github.com/lemire/crackingxoroshiro128plus](https://github.com/lemire/crackingxoroshiro128plus)

