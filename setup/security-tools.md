# Security & Monitoring Tools

A focused baseline for hardening, auditing, and visibility on a developer workstation.

## Intrusion detection: Fail2ban

**What it does:** parses auth logs and blocks repeated offenders.

Useful checks:

```bash
sudo systemctl start fail2ban
sudo fail2ban-client status
```

## System auditing: Lynis

**What it does:** runs a comprehensive host security audit and suggests remediations.

Install & run:

```bash
sudo apt install lynis -y
sudo lynis audit system
```

## Visibility & triage

**Failed logins (one‑off):**

```bash
sudo cat /var/log/auth.log | grep "Failed"
```

**Live auth log:**

```bash
sudo tail -f /var/log/auth.log
```

**Processes:**

```bash
htop
```

**Network listeners:**

```bash
sudo apt install net-tools
sudo netstat -tulpn
```

## Account isolation (browsers)

Create **separate profiles** for work, freelancing, and banking to isolate sessions and cookies.

Firefox Profile Manager:

```bash
firefox -P
```

## Recommended baseline

| Area        | Tool/Setting                |
|-------------|-----------------------------|
| Updates     | `apt update && apt upgrade` |
| Firewall    | `ufw`                       |
| IDS         | `fail2ban`                  |
| Auditing    | `lynis`                     |
| Monitoring  | `htop`, `netstat`, logs     |
| VPN         | ProtonVPN / Mullvad         |
| 2FA         | Authenticator app           |