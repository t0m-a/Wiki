# Technical Documentation Wiki

Welcome to my technical documentation wiki and system administration knowledge base. All documentation is organized into clean, hierarchical Markdown guides below.

---

## Documentation Index

| Topic | Summary | Full Guide |
| :--- | :--- | :--- |
| **Bash & Shell Scripting** | `for` loops, ANSI colors, standard streams (`STDIN`/`STDOUT`/`STDERR`), script arguments, `ps`, WSL backup, VMware batch | [bash.md](bash.md) |
| **Linux & Unix Tools** | `sed`, `echo`, `cut`, `grep` (including PHP backdoor detection), `find`, `cron`, `set`, `awk`, `IFS`, `rename`, `shred`, `rclone`, `rsync` | [linux-tools.md](linux-tools.md) |
| **Vi & Vim Basics** | Search and replace syntax and essential Vi/Vim keyboard shortcuts | [vi-basics.md](vi-basics.md) |
| **Useful Commands** | Network testing (`wget`, `curl`), NFS mounts, live log monitoring (`watch`, `ccze`, `lsof`), `systemctl`, package & process tips | [useful-commands.md](useful-commands.md) |
| **SSH, DSH, SCP, PTS & TTY** | Shell/Console/TTY/PTS concepts, SSH local port forwarding, `ssh-agent`, SSH key management, `dsh`, and `scp` | [ssh-pts-tty.md](ssh-pts-tty.md) |
| **Iptables & Network Management** | Packet capture (`tcpdump`), routing (`route`, `ip`, `arp`, `dig`), and `iptables` firewall rules & persistence | [iptables-and-network.md](iptables-and-network.md) |
| **Common SQL Commands** | MySQL connection, user/privilege management, `mysqldump` backups, cold backups, and automated daily backup script | [sql.md](sql.md) |
| **SSL, OpenSSL & HTTPS/HSTS** | Diffie-Hellman parameters, CSR & X.509 certificate inspection, `s_client` debugging, AES-256 encryption, Nginx TLS/HSTS | [ssl-tips-and-tricks.md](ssl-tips-and-tricks.md) |
| **Docker & Docker Compose** | Docker installation, CLI subcommands reference, container linking & volumes, `docker-compose.yml` stacks, and Kali `Dockerfile` examples | [docker.md](docker.md) |
| **Git, GitHub & Atom Memo** | Core Git workflow, safe vs. hard resets, repo initialization, history cleanup (`filter-branch`), and Atom editor tips | [git-and-github.md](git-and-github.md) |
| **Go (Golang)** | Go installation, `GOPATH`, CLI commands, `fmt` verbs, custom packages, `iota` constants, closures, and pointers | [go-golang.md](go-golang.md) |
| **LDAP & Useful Resources** | `ldapsearch` administration queries and curated Linux, security, and networking links | [ldap-and-resources.md](ldap-and-resources.md) |

---

## Topic Overviews & Quick Reference

### 1. [Bash & Shell Scripting](bash.md)
Covers the essentials of Bash and shell scripting on Linux/Unix systems, including loops, positional arguments, standard I/O streams, and terminal color codes.

```bash
for i in $(cmd); do cmd $i; done
for i in $(docker images | awk '{print $3}' | grep -v IMAGE); do echo $i; done
```

➡️ **[Read full Bash & Shell Scripting guide](bash.md)**

---

### 2. [Linux & Unix Command-Line Tools](linux-tools.md)
Reference memo on standard Linux and Unix command-line utilities used in daily system administration:
`sed`, `echo`, `cut`, `grep`, `find`, `cron`, `set`, `awk`, `rename`, `shred`, `rsync`, `rclone`, and more.

➡️ **[Read full Linux & Unix Tools guide](linux-tools.md)**

---

### 3. [Vi & Vim Basics](vi-basics.md)
Quick reference for the Vi/Vim text editor.

**Replace a string in a file:**

```vim
:i,$ s/string-to-replace/string-used-for-replacement
```

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + V` | Visual block edit |
| `Ctrl + A` / `Ctrl + X` | Increment / decrement number under cursor by `1` |
| `G` / `g` | Go to End of File (EOF) / Beginning of File (BOF) |
| `O` / `o` | Add line above / below |
| `/` | Search |
| `Esc + U` | Undo (`Ctrl + Z`) |
| `d` / `d$` | Delete line / delete to end of line |

➡️ **[Read full Vi & Vim Basics guide](vi-basics.md)**

---

### 4. [Useful Miscellaneous Commands](useful-commands.md)
Miscellaneous commands for Linux/Unix networking, NFS, log monitoring, process management, and system administration.

```bash
# Watch established connections between two hosts
watch -d -n 3 "netstat -ap | grep `hostname`:4444[1-4] | grep ESTABLISHED"

# Watch reverse proxy access logs for today's date
cd /logs && for s in `ls -lrt *_access_log | grep " $(date "+%b %d")" | grep -v servername | awk '{print $9}'`; do flog $s; done
```

➡️ **[Read full Useful Commands guide](useful-commands.md)**

---

### 5. [SSH, DSH, SCP, PTS & TTY](ssh-pts-tty.md)
- **Terminal vs. Console vs. Shell:** The terminal connects to the console where the shell is presented.
- **TTY (Teletypewriter):** Virtualized console ports accessible via `Ctrl + Alt + F1..F12` (viewable with `who`).
- **PTS (Pseudo Terminal Slave):** Emulated TTY devices used for network terminal sessions such as **SSH** and **Telnet**.

Includes SSH tunneling (`ssh -L`), `ssh-agent`, SSH key passphrase management, Distributed Shell (`dsh`), and Secure Copy (`scp`).

➡️ **[Read full SSH, PTS & TTY guide](ssh-pts-tty.md)**

---

### 6. [Iptables & Network Management](iptables-and-network.md)
Frequently used commands for packet capture (`tcpdump`), routing (`route`, `ip route`, `arp`, `dig`), and managing `iptables` firewalls on Linux servers.

➡️ **[Read full Iptables & Network Management guide](iptables-and-network.md)**

---

### 7. [Common SQL Commands](sql.md)
Frequently used SQL/MySQL commands for database inspection, user and privilege management, `mysqldump` exports/imports, cold file-level backups, and an automated daily backup script.

➡️ **[Read full Common SQL Commands guide](sql.md)**

---

### 8. [SSL, OpenSSL & HTTPS/HSTS Tips and Tricks](ssl-tips-and-tricks.md)
OpenSSL CLI commands for generating 4096-bit Diffie-Hellman keys, inspecting CSRs and X.509 certificates, debugging TLS handshakes with `openssl s_client`, encrypting files with AES-256-CBC, and configuring HTTPS/HSTS in Nginx.

➡️ **[Read full SSL Tips and Tricks guide](ssl-tips-and-tricks.md)**

---

### 9. [Docker & Docker Compose Administration](docker.md)
Notes from Docker administration and advanced container management trainings: installation, CLI reference, container networking & volume persistence, `docker-compose.yml` LEMP stacks, and Kali Linux `Dockerfile` examples with X11 GUI forwarding.

➡️ **[Read full Docker Administration guide](docker.md)**

---

### 10. [Git, GitHub & Atom Memo](git-and-github.md)
Handy reminders for core Git workflows, resetting changes (`--soft` + `stash` vs. `--hard`), global configuration, and purging folders from local and remote history (`git filter-branch`).

➡️ **[Read full Git & GitHub Memo](git-and-github.md)**

---

### 11. [Go (Golang) Programming Notes](go-golang.md)
Notes and annotated code examples from Todd McLeod's Go programming course, covering cross-compilation, workspace setup (`GOPATH`), packages, `fmt` formatting verbs, variables, constants (`iota` and bit shifting), closures, and pointers.

➡️ **[Read full Go (Golang) guide](go-golang.md)**

---

### 12. [LDAP Administration & Useful Resources](ldap-and-resources.md)
`ldapsearch` command-line examples and a curated list of Linux, terminal, HTTP, and security resources.

```bash
ldapsearch -D "cn=LDAP DIRECTORY SERVER" -w PASSWD -v -p PORT -b "ou=O_UNIT" "cn=CANON_NAME"
ldapsearch -D "cn=LDAP DIRECTORY SERVER" -w PASSWD -v -p PORT -b "o=ORGANISATION" "cn=CANON_NAME CANONICAL NAMES"
```

➡️ **[Read full LDAP & Useful Resources guide](ldap-and-resources.md)**

---

*Author: **Thomas Simon** ([tsimon.me](https://tsimon.me) · [GitHub](https://github.com/t0m-a) · [Docker Hub](https://hub.docker.com/u/simonthomas/) · [LinkedIn](https://www.linkedin.com/in/thomas-simon-bolivie/?locale=en_US) · [Twitter](https://twitter.com/7ohms))*
