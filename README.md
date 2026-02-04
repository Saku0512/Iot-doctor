# IoT Doctor

A security diagnostic and educational tool for home IoT devices.

> **KOSEN Programming Contest - Open Category**

## Overview

IoT Doctor enables general household users to understand the security status of their IoT devices without specialized knowledge and take concrete remediation actions.

### Key Features

- **Network Scan** - Auto-detect devices on local network
- **Device Identification** - Identify vendor/model from MAC address and fingerprint
- **Vulnerability Check** - Detect default passwords, open ports, outdated firmware
- **Security Score** - Visualize overall safety as 0-100 score
- **Japanese Report** - Easy-to-understand results without jargon
- **Remediation Guide** - Step-by-step fix instructions per issue

### Differentiation

| Aspect | Existing Tools | IoT Doctor |
|--------|----------------|------------|
| Target Users | Security experts | General household users |
| Language | English-centric | Japanese UI, domestic product support |
| Scope | Detection only | Detection → Remediation → Education |
| Usability | CLI / Expert UI | One-click diagnosis |

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | Tauri v2 |
| Frontend | Svelte + TailwindCSS |
| Backend | Rust |
| Scan Tools | nmap + rustscan (bundled) |
| Local DB | SQLite |
| Target OS | Windows / macOS / Linux |

## Scan Levels

### Level 1: Passive Information Gathering
- Device discovery (ARP scan)
- MAC address vendor identification
- Hostname detection (mDNS / NetBIOS)
- OS estimation (TTL analysis)

### Level 2: Active Scanning
- Open port detection (TCP SYN scan)
- Service identification (banner grabbing)
- Encryption status (TLS/SSL verification)
- Firmware version detection

### Level 3: Vulnerability Verification (Requires Consent)
- Default password check
- Admin panel access verification
- Telnet/SSH credential testing
- UPnP vulnerability probing

## Project Structure

```
iot-doctor/
├── src-tauri/
│   ├── src/
│   │   ├── main.rs
│   │   ├── lib.rs
│   │   ├── scanner/          # Scan logic
│   │   ├── database/         # DB operations
│   │   ├── vulndb/           # Vulnerability DB
│   │   └── report/           # Report generation
│   └── binaries/             # Bundled nmap, rustscan
├── src/
│   ├── lib/
│   │   ├── components/       # Svelte components
│   │   ├── stores/           # State management
│   │   └── utils/
│   └── routes/
├── package.json
└── tailwind.config.js
```

## Development

### Prerequisites

- Node.js 18+
- Rust 1.70+
- nmap
- rustscan

### Setup

```bash
# Clone repository
git clone https://github.com/Saku0512/iot-doctor.git
cd iot-doctor

# Install dependencies
npm install

# Run in development mode
npm run tauri dev

# Build for production
npm run tauri build
```

## Roadmap

- [x] Requirements specification
- [ ] Tauri project setup
- [ ] Level 1 implementation (device discovery)
- [ ] Level 2 implementation (port scanning)
- [ ] Level 3 implementation (vulnerability verification)
- [ ] Security scoring system
- [ ] Japanese report generation
- [ ] Educational content
- [ ] Cross-platform builds

## License

TBD

## Team

KOSEN Programming Contest Entry
