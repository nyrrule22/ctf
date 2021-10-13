# Enumeration

## Shell Upgrade

```bash
# Check /bin directory if know tools come up in the PATH (i.e. which python)
import pty;pty.spawn("/bin/bash");
ctrl+z
stty raw -echo
fg
export TERM=xterm
```

## Checks

### Commands

Use `sudo -l` to check if commands can be run as another use i.e. root

Use `find` to look for SUID and GUID files we may be able to execute







