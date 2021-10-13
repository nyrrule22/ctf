# Enumeration

## Linux

### Shell Upgrade

```bash
# Check /bin directory if no tools come up in the PATH (i.e. which python)
python -c 'import pty;pty.spawn("/bin/bash")';
ctrl+z
stty raw -echo
fg
export TERM=xterm
```

### Checks

#### Manual

* Check /etc/passwd for users
* Check /etc/shadow for passwords
* Browse filesystem looking for non-standard layout, directories, files

#### Commands

* Use `sudo -l` to check if commands can be run as another use i.e. root
* Use `find` to look for SUID and GUID files we may be able to execute
* Use `crontab` to look for any scheduled jobs

#### Scripts

* LinPEAS

### Exploitation

#### Modifiable Bash Script Owned/Running by Root

Edit by adding a reverse shell command. Listen on `nc` and wait to be executed.









