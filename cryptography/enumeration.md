# Enumeration

## Hashing

### Checks

#### Non-Cryptographic Hash

crc32

### Types

#### Non-Cryptographic Hashing Algorithm

* crc32
  * Ex: Found 891568578 to equal abc
  * Need to convert the integer to Hex followed by 8 zeros. Ex: with unknown admin password
    * `python hex(-432570933 % (1<<32))`
      * '0xe6377dcb' 
        * `echo "e6377dcb:00000000" > hash.txt`
    * `hashcat -a 0 -m 11500 hash.txt -r rules/oneruletorule.rule rockyou.txt`
      * oqllo7 is the outputted password
