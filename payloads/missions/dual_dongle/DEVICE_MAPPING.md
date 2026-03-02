# Dual Dongle Setup

## Device Assignment

| Dongle | IP | Purpose | Payloads |
|--------|-----|---------|----------|
| **TDongle S3 #1** | 4.3.2.1 | Recon & Exfil | Windows/Linux quick grabs |
| **Waveshare S3** | 4.3.2.2 | Network Attacks | WiFi deauth, Evil Twin |

## Attack Scenarios

### Scenario 1: Split Attack
- **Dongle 1:** Physical access - Password extraction
- **Dongle 2:** Network access - WiFi reconnaissance

### Scenario 2: Relay Attack
- **Dongle 1:** Capture traffic on USB
- **Dongle 2:** Relay traffic to remote C2

### Scenario 3: Persistence
- **Dongle 1:** Quick grab (15s)
- **Dongle 2:** Long-term persistence

## Network Configuration

Both devices use:
- Network: 4.3.2.0/24
- Gateway: 4.3.2.1 (first dongle)
- Web UI: :8080

## Payload Distribution

### TDongle S3 #1 (4.3.2.1)
- `windows/exfil/passwords_quick.ds` - 10s grab
- `linux/exfil/passwords_quick.ds` - 10s grab
- `recon/network_recon.ds` - Network scan

### Waveshare S3 (4.3.2.2)
- `wifi/deauth.ds` - WiFi deauth
- `wifi/handshake.ds` - Handshake capture
- `bluetooth/recon.ds` - Bluetooth scan
