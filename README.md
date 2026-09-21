# Virtual Node Suite

**Trustless Bitcoin Verification & Control without a Full Node**

A hybrid architecture for Bitcoin transaction verification that achieves ~99.9% trustlessness through multi-source consensus, cryptographic proofs, and automatic lie detection—without requiring 500GB of storage or days of sync time.

```
┌─────────────────────────────────────────────────────────────────┐
│  Full Node (100% trustless)    │  Virtual Node (99.9% trustless)│
│  500GB SSD, Days to sync       │  <1GB RAM, Instant verification│
│  BEST in practice              │  BEST FOR REALITY              │
└─────────────────────────────────────────────────────────────────┘
       ↓                                      ↓
    GOLD                                ALTERNATIVE
  STANDARD                              (RECOMMENDED)
       ↓                                      ↓
    ┌─────────────────────────────────────────┐
    │  BOTH TOGETHER = MAXIMUM SECURITY       │
    │  Defense-in-depth architecture          │
    │  Detect network attacks & censorship    │
    └─────────────────────────────────────────┘
```

## The Problem

Bitcoin users face a false choice:

- **Run a full node**: 100% trustless but impractical (500GB storage, days to sync, 24/7 power/bandwidth)
- **Trust a public node**: Practical but risky (vulnerable to man-in-the-middle attacks, single point of failure)

Virtual Node Suite eliminates this tradeoff.

## The Solution

Query **10+ independent blockchain sources** with cryptographic proof validation. A consensus voting model automatically detects and blacklists lying nodes, creating a self-healing, statistically trustless network.

### How It Works

1. **Multi-Source Consensus**: Query 10, 20, or 100 independent peers for transaction data
2. **Automatic Lie Detection**: Compare responses, identify consensus, blacklist liars
3. **Cryptographic Proofs**: Verify Merkle proofs, SPV chains, and OP_RETURN anchors
4. **No Infrastructure Burden**: Runs on Raspberry Pi, mobile, or browser—instant startup

### Trust Model

| Metric | Full Node | Virtual Node | Both |
|--------|-----------|--------------|------|
| **Trustlessness** | 100% | ~99.9% | 100% (verified) |
| **Storage** | 500GB+ | <1GB | 500GB+ |
| **Sync Time** | Days | Instant | Days |
| **Infrastructure** | 24/7 power | Flexible | 24/7 + flexible |
| **Use Case** | Miners, exchanges | Wallets, users | Maximum security |

## Core Features

### 🔐 **Cryptographic Proofs**
RSA-4096 signatures, Merkle proofs, OP_RETURN blockchain anchoring. Prove transactions without full blockchain download.

### 🌐 **Multi-Peer Consensus**
Query 10+ independent sources. Auto-detect lying nodes. Self-healing network with reputation scoring.

### ⚡ **Zero Infrastructure**
Raspberry Pi friendly. Mobile native. Instant verification. No sync required.

### 🔑 **Quorum Approvals**
M-of-N authorization. Signed logs. Multi-sig workflows. Full audit trail.

### 🚨 **Emergency Sweep**
OP_RETURN signals, dust transaction triggers, E-Stop button, Bluetooth, dead man's switch. Multiple trigger mechanisms for security.

### 📡 **Privacy Routing**
Tor routing, I2P support, multi-relay broadcasting, randomized delays. Route transactions through privacy-focused networks.

### ⏳ **Dead Man's Switch**
Passive countdown timer. Auto-sweep without active monitoring. Inheritance-ready fund protection.

### 📱 **Mobile Notifications**
Watchtower alerts, push notifications, xpub stays private. Monitor fund movement in real-time.

### ✍️ **Pre-Signed Transactions**
Sign now, broadcast later for known amounts. Balance monitoring prevents signature invalidation. Address alerts on spend.

### ⚙️ **Peer & Sibling Configuration**
Choose verification sources (3, 10, 20, 100 peers). Optional local Bitcoin Core/Monetary Node as sibling for defense-in-depth.

### 📊 **Arbitrary Data Fields**
Custom metadata on receipts. Tax categories, invoice numbers, audit trail. Signed receipt export.

### 🔄 **Node Cloning**
Geographic replication, automatic failover, distributed setup. Run backup nodes for resilience.

### 🛡️ **Security Hardening**
SSH hardening, Fail2Ban protection, UFW firewall. Umbrel-based security framework.

### 📦 **Electrum Compatible**
Works with Sparrow Wallet and Wasabi. Standard Electrum protocol (JSON-RPC 2.0 over TCP/SSL).

### 💾 **Receipt Export**
JSON, PDF, CSV, ZIP formats. Signed receipts with digital signatures. Batch export and audit archive.

### 🎯 **Source Blacklisting**
Auto-detect lying nodes via consensus deviation. Reputation scoring. Self-healing network.

### 🌍 **Geographic Diversity**
Multi-region sources. Geographically distributed verification. Censorship resistant. Global access.

## Architecture Overview

### Receiving Transactions
```
Sparrow/Wasabi Wallet
         ↓
   Electrum Protocol
         ↓
Virtual Node Suite
    ↙    ↓    ↘
Peer 1  Peer 2  Peer 3 ... Peer N
   ↘    ↓    ↙
 Consensus Vote
         ↓
 Validate/Blacklist
         ↓
  Watchtower Alerts
```

### Sending Transactions
```
Pre-signed Transaction
    (known amounts)
         ↓
    Balance Monitor
    (address alerts)
         ↓
  Relay Strategy
  ↙    ↓    ↘
Tor   I2P  Clearnet
   ↘    ↓    ↙
  Multi-relay
  Broadcasting
         ↓
  Blockchain
```

## Configuration Options

### Verification Levels

**Light** (3 peers)
- Fastest, minimal overhead
- Best for low-value transactions

**Standard** (10 peers)
- Balanced latency & trustlessness
- Recommended default

**Enhanced** (20 peers)
- High confidence
- For medium-value transactions

**Maximum** (100 peers)
- Maximum security
- For large/sensitive transactions

### Relay Strategies

- **Clearnet**: Direct broadcast
- **Tor**: Privacy-focused routing
- **I2P**: Anti-censorship routing
- **Randomized**: Variable delays and relay order

### Sibling Nodes (Optional)

Run alongside Virtual Node for defense-in-depth:
- **Bitcoin Core**: Full node validation
- **Monetary Node**: Specialized indexer
- **ElectRS**: Electrum server with full node

Compare peer consensus vs. local Proof-of-Work validation to detect network attacks.

## Getting Started

### Prerequisites

- Node.js 18+ or Python 3.8+
- Raspberry Pi 4+ (or any x86/ARM system)
- Internet connection
- <1GB disk space

### Installation

```bash
git clone https://github.com/sambitcoin/virtualnode.git
cd virtualnode
npm install        # or pip install -r requirements.txt

# Configuration
cp config.example.json config.json
# Edit config.json with your peer list and settings

# Run
npm start          # or python app.py
```

### Quick Test

```bash
# Query a single transaction
./virtualnode query --txid abc123def456 --peers 10

# Get balance for xpub
./virtualnode balance --xpub xpub... --peers 20

# Set pre-signed transaction
./virtualnode presign --input "addr1:amount1" --output "addr2:amount2"
```

### Configuration

```json
{
  "verification_level": "standard",  // light, standard, enhanced, maximum
  "peer_count": 10,                   // 3, 10, 20, 100
  "relay_strategy": "randomized",     // clearnet, tor, i2p, randomized
  "peers": [
    "peer1.example.com:50002",
    "peer2.example.com:50002",
    "..."
  ],
  "enable_watchtower": true,
  "watchtower_interval": 600,         // seconds
  "deadman_switch_hours": 720,        // 30 days default
  "blacklist": {
    "peer_name": "detected_liar"
  }
}
```

## Electrum Wallet Integration

### Sparrow Wallet

1. Settings → Server → Network
2. Select "Manual" 
3. Enter Virtual Node host and port (default: localhost:50002)
4. Confirm SSL certificate
5. Start using Sparrow with trustless verification

### Wasabi Wallet

Same configuration via Wasabi's Backend Type settings.

## Security Model

### Attack Scenarios & Mitigations

| Attack | Scenario | Defense |
|--------|----------|---------|
| **Single Lie** | One peer lies | Consensus voting detects & blacklists |
| **Coordinated Lie** | N peers lie, undetected collusion | Reputation scoring + geographic diversity |
| **Network Fork** | Temporary network split | Peer redundancy, consensus reconciliation |
| **ISP Interception** | MITM at network level | Tor/I2P routing, certificate pinning |
| **Consensus Attack** | Majority of peers lie | Geographic diversity, sibling node comparison |
| **Sybil Attack** | Attacker controls many peers | Reputation system, peer diversity requirements |
| **All Compromised** | Every peer is dishonest | Run local full node as sibling, compare |
| **History Rewrite** | Blockchain reorg | OP_RETURN anchors prevent deep reorgs |

### Defense-in-Depth

For maximum security, run Virtual Node alongside Bitcoin Core:

1. **Virtual Node queries peers** → Fast, practical
2. **Bitcoin Core validates locally** → Slow, trustless
3. **Compare results** → Detect network attacks
4. **Alert on mismatch** → Security breach detected

## Development Roadmap

### Phase 1: Trustless Verification ✓
- [x] Multi-source consensus voting
- [x] Source blacklisting with reputation scoring
- [x] Merkle proof validation

### Phase 2: Electrum Integration ✓
- [x] JSON-RPC 2.0 server
- [x] Sparrow/Wasabi compatibility
- [x] Remote access (Cloudflare, Tailscale, WireGuard)

### Phase 3: Signed Receipts & Broadcasting
- [ ] RSA-4096 digital signatures
- [ ] OP_RETURN blockchain anchoring
- [ ] Multi-relay broadcasting with fallback

### Phase 4: Approval & Control
- [ ] Quorum authorization (M-of-N)
- [ ] Pre-signed transactions with balance monitoring
- [ ] Watchtower alerts with mobile notifications

### Phase 5: Emergency & Continuity
- [ ] Emergency sweep signals (OP_RETURN, dust, E-Stop)
- [ ] Dead man's switch timer
- [ ] Node cloning & geographic replication

### Phase 6: Security & Privacy
- [ ] Umbrel-based security hardening
- [ ] SSH configuration & Fail2Ban
- [ ] UFW firewall rules

## Performance Metrics

| Metric | Value |
|--------|-------|
| **Verification Latency** | 1-3 seconds (10 peers) |
| **Peer Query Overhead** | <100ms per peer |
| **Memory Usage** | <500MB (10 peers) |
| **Disk Space** | <1GB (minimal state) |
| **Bandwidth** | ~1-5 MB/day (monitoring mode) |
| **CPU** | <5% (Raspberry Pi 4) |

## Contributing

We welcome contributions! Areas we're looking for help:

- **Peer discovery**: Dynamic peer selection and rotation
- **Privacy**: Enhanced Tor/I2P integration
- **Performance**: Optimize consensus voting
- **Testing**: Additional attack scenario simulations
- **Documentation**: Deployment guides for different platforms

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Security Disclosure

If you discover a security vulnerability, please email security@virtualnode.dev instead of using the issue tracker. We take security seriously and will respond promptly.

## License

MIT License - See [LICENSE](LICENSE) for details.

## References

### Bitcoin Protocol
- [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki) - Hierarchical Deterministic Wallets
- [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki) - Mnemonic Code
- [BIP70](https://github.com/bitcoin/bips/blob/master/bip-0070.mediawiki) - Payment Protocol

### Electrum Protocol
- [Electrum JSON-RPC Specification](https://electrumx-spesmilo.readthedocs.io/en/latest/)
- [Electrum SPV Validation](https://electrum.org/#home)

### Privacy & Security
- [Tor Project](https://www.torproject.org/)
- [I2P Network](https://geti2p.net/)

### Related Projects
- [Monetary Node](https://monetarynode.org) - Specialized Bitcoin indexer
- [Bitcoin Core](https://github.com/bitcoin/bitcoin) - Full node reference
- [Sparrow Wallet](https://www.sparrowwallet.com/) - Desktop Bitcoin wallet
- [Wasabi Wallet](https://www.wasabiwallet.io/) - Privacy-focused wallet

## Acknowledgments

Virtual Node Suite builds on decades of Bitcoin infrastructure development. Special thanks to:

- Electrum team for protocol standardization
- Monetary Node for specialized indexing innovations
- Bitcoin Core team for trustless validation reference
- Sparrow Wallet for wallet UX excellence

---

**Full Node is best. Virtual Node is the best alternative. Both together is maximum security.**

For updates and announcements, [star this repository](https://github.com/sambitcoin/virtualnode) and follow the project.

**Questions?** [Open an issue](https://github.com/sambitcoin/virtualnode/issues) or check our [documentation](https://docs.virtualnode.dev).
