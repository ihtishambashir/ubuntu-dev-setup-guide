# System Essentials (Ubuntu)

A quick, practical set of commands for keeping your system patched, watching authentication activity, and checking what’s running.

## Updates

```bash
sudo apt update && sudo apt upgrade -y
```

## Authentication log (failed attempts)

```bash
sudo cat /var/log/auth.log | grep "Failed"
```

## Authentication log (live tail)

```bash
sudo tail -f /var/log/auth.log
```

## Fail2ban basics

```bash
sudo systemctl start fail2ban
sudo fail2ban-client status
```

## Browser profile isolation (Brave/Firefox)

Use separate profiles for different contexts (e.g., GitHub, Fiverr, banking) to isolate cookies and sessions.

Launch Firefox Profile Manager:

```bash
firefox -P
```

## Encrypt your home directory

```bash
sudo apt install ecryptfs-utils
ecryptfs-migrate-home -u $USER
```

> If you already use full‑disk encryption, per-user home encryption may be unnecessary.

## Continuous monitoring

Install and run **Lynis** (security auditing):

```bash
sudo apt install lynis -y
sudo lynis audit system
```

View processes:

```bash
htop
```

Network listeners:

```bash
sudo apt install net-tools
sudo netstat -tulpn
```

## Quick reference

| Category            | Tool/Command                  | Purpose                   |
|--------------------|-------------------------------|---------------------------|
| System Updates     | `apt update && apt upgrade`   | Stay patched              |
| Firewall           | `ufw`                         | Block unauthorized access |
| Intrusion Detection| `fail2ban`, `lynis`           | Detect & block attacks    |
| Browser Isolation  | Brave/Firefox profiles        | Keep accounts separate    |
| VPN                | ProtonVPN / Mullvad           | Encrypt traffic           |
| 2FA                | Authenticator app             | Secure logins             |
| Monitoring         | `htop`, `netstat`, `auth.log` | Watch system behavior     |