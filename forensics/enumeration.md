# Enumeration

### Checks

#### Assumes a PCAP file given

* Use Wireshark to open the file
* Check the TCP stream
  * Check for interesting information like patterns, code, SQL, credentials, etc.

#### Assumes memory dump file given

* Verify filetype: `file memdump.vmem`
* Use `strings` to parse file: `strings -n 10 memdump.vmem`
  * Try to grep out certain strings like password, 
* Check Volatility: HackTricks CheatSheet
  * Discover profile
    * `volatility imageinfo -f memdump.vmem`
    * `volatility kdbgscan -f memdump.vmem`
    * You can also download profiles from GitHub or aldeid as mentioned
      * `strings memdump.vmem | grep -i 'Linux version' | uniq`
    * Check for 
