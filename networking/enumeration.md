# Enumeration

## Port Knocking

Port Knocking is a method of externally opening ports by generating a connection on a set of prespecified closed ports.

* You can use `knockd` to execute the port knocking
  * `knockd 10.10.10.10 1337 68 61 78`
* You can use `knock` to execute the port knocking
  * `knock 10.10.10.10 1337 68 61 78`
* You can use `nmap` to execute the port knocking
  * `for x in 1337 68 61 78; do nmap -Pn --max-retries 0 -p $x 10.10.10.10; done`
* You can use `nc` to try to connect to the newly found open port
  * `nc 10.10.10.10 2021`
    * Try to execute OS commands
