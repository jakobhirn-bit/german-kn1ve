# Dual Dongle Attack Framework

## Overview

This framework enables coordinated attacks using two USB Army Knife devices simultaneously.

## Device Roles

| Role | Dongle | Network | Purpose |
|------|--------|---------|---------|
| **Primary** | TDongle S3 #1 | USB + 4.3.2.1 | Physical access, USB injection |
| **Secondary** | Waveshare S3 | WiFi + 4.3.2.2 | Network attack, WiFi relay |

## Attack Matrix

| Attack Type | Dongle 1 | Dongle 2 | Duration |
|-------------|----------|----------|----------|
| Quick Grab | passwords_quick | - | 10s |
| Full Extract | browser_full | network_sniff | 60s |
| Stealth | stealth_extraction | - | 90s |
| Persistent | persistence_relay | WiFi beacon | 10s |
| Coordinated | passwords_quick | wifi/deauth | 30s |

## Deployment

### Physical Access Only
```
Use: Dongle 1 only
Payloads: windows/exfil/*, linux/exfil/*
```

### Physical + Network
```
Use: Both Dongles
Payloads: dual_dongle/coordinated_attack.ds
Dongle 1: USB to target
Dongle 2: Near target network
```

### Stealth Operation
```
Use: Both Dongles, staggered
Payloads: dual_dongle/stealth_extraction.ds
Phase 1: Dongle 1 extracts (90s)
Phase 2: Dongle 2 exfiltrates via WiFi
```

## Network Configuration

### Dongle 1 (Primary)
```
IP: 4.3.2.1
Gateway: 4.3.2.1
Web UI: http://4.3.2.1:8080
```

### Dongle 2 (Secondary)
```
IP: 4.3.2.2
Gateway: 4.3.2.1
Web UI: http://4.3.2.2:8080
```

## Payload Loading

1. Connect Dongle 1 to target
2. Wait for web UI (4.3.2.1:8080)
3. Upload payload via web interface
4. (Optional) Connect Dongle 2 for network attacks
5. Execute payload

## Security Notes

- Both devices use German keyboard layout
- Web UI accessible only from USB network
- No persistence after reboot (unless configured)
- Traffic encrypted between dongles
