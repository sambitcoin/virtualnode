# Virtual Node - Feature Roadmap

Complete trustless Bitcoin verification system with multi-source consensus voting, wallet management, Sparrow integration, and peer node network.

---

## 📋 Phase 1: Core Infrastructure & Database

### Database Layer
- [x] SQLAlchemy 2.0 ORM models (12 tables)
- [x] BlockchainSource table - track external sources with reputation
- [x] ConsensusResult table - store voting outcomes
- [x] SourceEvent table - audit trail for source behavior
- [x] Wallet table - HD wallet storage
- [x] WalletAddress table - derived address tracking
- [x] UTXO table - unspent output management
- [x] Transaction table - pending/confirmed tx storage
- [x] ActivityLog table - complete audit log
- [x] Automatic timestamps (created_at, updated_at)
- [x] Transaction support with rollback
- [x] Index optimization for queries

### Consensus Engine
- [x] Byzantine Fault Tolerance voting (quorum-based)
- [x] Source reputation scoring (0-100)
- [x] Weighted voting power based on reputation
- [x] Confidence scoring (0-100%)
- [x] Consensus threshold configuration
- [x] Malicious source detection & flagging
- [x] Source blacklisting after repeated failures
- [x] Age-weighted node age factor
- [x] Uptime percentage tracking
- [x] Source reliability metrics

### Blockchain Sources
- [x] Multi-source adapter pattern
- [x] Blockcypher API integration
- [x] Blockchain.com API integration
- [x] Bitcoin Core RPC integration
- [x] Async HTTP requests (aiohttp)
- [x] Error handling & retry logic
- [x] Response time tracking
- [x] Source health monitoring
- [x] Query caching to reduce API calls

### Wallet Management
- [x] HD wallet support (BIP32/BIP44)
- [x] xpub import for watch-only wallets
- [x] Address derivation (m/84'/0'/0'/0/n)
- [x] UTXO tracking & management
- [x] Balance calculation from UTXOs
- [x] Transaction building (PSBT support)
- [x] Fee estimation
- [x] Address labeling
- [x] Wallet encryption support framework
- [x] Multi-wallet management

---

## 🔗 Phase 1.5: P2P Node Discovery & Network

### Node Discovery
- [x] DNS seed integration (8 seeds)
- [x] Hardcoded bootstrap peers
- [x] Peer exchange protocol (PEX)
- [x] Node reputation tracking
- [x] Geographic diversity scoring
- [x] Automatic peer rotation for privacy

### P2P Node Management
- [x] TCP connection management
- [x] Connection timeout handling
- [x] Connection pooling (min 10, max 100 nodes)
- [x] Node status tracking (connected/disconnected/failed/blacklisted)
- [x] Node type detection (full node, SPV, relay, etc.)
- [x] Block height tracking per node
- [x] Latency measurement (exponential moving average)
- [x] Stale node detection (5min timeout)
- [x] Graceful disconnect handling

### Node Scoring & Selection
- [x] Composite scoring algorithm (0-100)
  - 40% success rate
  - 30% uptime/reliability
  - 15% latency
  - 15% accuracy/consensus agreement
- [x] Age bonus (connection duration)
- [x] Malicious flag penalties
- [x] Automatic blacklisting (3+ flags)
- [x] Query history tracking (last 1000)
- [x] Best node selection
- [x] Diverse node selection (Byzantine consensus)
- [x] Network health scoring

### Node Privacy & Rotation
- [x] Privacy rotation strategy (disconnect old → connect new)
- [x] Least reliable rotation
- [x] Oldest connection rotation
- [x] Subnet diversity (first 3 IP octets)

---

## 🎨 Phase 2: Dashboard & UI

### Dashboard UI (Synthwave Aesthetic)
- [x] Glass morphism effect (frosted glass backdrop)
- [x] Neon color scheme (cyan #00f3ff, green #00ff41, pink #ff007f)
- [x] CRT scanline effect
- [x] Floating particle animations
- [x] Tailwind CSS + custom Canvas effects
- [x] Dark theme optimization
- [x] Responsive design (mobile-first)
- [x] Real-time stats updates

### Terminal Display
- [x] Matrix-style character decoder animation
- [x] 4-second decode duration per line
- [x] Random character pool (alphanumeric + Unicode symbols)
- [x] Color-coded event types:
  - Cyan: BLOCK
  - Pink: CONSENSUS
  - Yellow: TRANSACTION
  - Green: PEER
  - Orange: WALLET
  - Blue: FEE
  - Red: ERROR
- [x] Auto-scrolling terminal (last 15 events)
- [x] Timestamp tracking per event
- [x] Event type badges
- [x] Live stat cards below terminal

### Dashboard Tabs
- [x] Sources tab - blockchain source status
- [x] Wallets tab - wallet management
- [x] UTXOs tab - unspent output browser
- [x] Build TX tab - transaction builder
- [x] Pending TXs tab - transaction queue
- [x] Settings tab - configuration
- [x] Logs tab - complete activity log

### Real-Time Updates
- [x] Block verification events
- [x] Byzantine voting updates
- [x] Transaction processing
- [x] Peer management (connect/disconnect/rotate)
- [x] Wallet operations
- [x] Network fee tracking
- [x] BTC price updates
- [x] Mempool statistics

---

## 🖥️ Phase 2.5: CLI Terminal Interface

### Virtual Node CLI
- [x] ANSI color-coded output
- [x] C++/Linux-style formatting
- [x] Real-time event streaming
- [x] Block verification simulation
- [x] Byzantine consensus voting display
- [x] Transaction processing pipeline
- [x] Peer connection management
- [x] Wallet operations tracking

### Event Types in Terminal
- [x] Block verification (block height, miner, tx count, reward)
- [x] Consensus voting (peer agreement %, confidence)
- [x] Transaction processing (tx ID, size, fee, value)
- [x] Peer management (connect/disconnect/rotate with reputation)
- [x] Wallet operations (import, balance check, address derivation, signing)
- [x] Network stats (mempool size, pending txs, fees)
- [x] Price tracking (BTC/USD with trends)

### System Status Display
- [x] Current block height
- [x] Active peer count
- [x] Pending transaction count
- [x] Mempool size in MB
- [x] Network fee in sat/vB
- [x] BTC price in USD
- [x] Consensus agreement %
- [x] Wallet balance

---

## 🔌 Phase 3: Sparrow Wallet Integration

### Sparrow Integration
- [x] PSBT (Partially Signed Bitcoin Transaction) support
- [x] Descriptor export/import
- [x] Wallet descriptor validation
- [x] Watch-only wallet import
- [x] Signature verification
- [x] Transaction export to Sparrow format
- [x] Sparrow import instructions UI
- [x] Connection setup guide

### Descriptor Format Support
- [x] wpkh() - native SegWit
- [x] sh(wpkh()) - SegWit wrapped
- [x] tr() - Taproot support framework
- [x] Multi-sig descriptor parsing

### Wallet Interop
- [x] xpub/ypub/zpub import
- [x] Derivation path validation
- [x] Address synchronization
- [x] UTXO confirmation checking
- [x] Transaction signing coordination

---

## ⚙️ Phase 4: Configuration & Deployment

### Configuration System
- [x] JSON config file (config.json)
- [x] Blockchain sources configuration
- [x] Bitcoin Core RPC endpoints
- [x] Pleb node peer list
- [x] Consensus parameters
  - Peer count target
  - Confidence threshold
  - Flag threshold
  - Node age weight factor
- [x] Database URL configuration
- [x] Port configuration (default 8000)

### REST API (FastAPI)
- [x] `/health` - health check
- [x] `/sources` - list all sources with reputation
- [x] `/sources/{name}` - specific source details
- [x] `/sources/{name}/history` - source event history
- [x] `/query` - execute consensus query
- [x] `/consensus/recent` - recent voting results
- [x] `/stats` - system statistics
- [x] `/terminal` - serve terminal dashboard
- [x] `/dashboard.html` - serve web dashboard
- [x] CORS middleware enabled
- [x] 25+ endpoints total

### Deployment
- [x] tmux orchestration (run.sh)
- [x] Multi-window setup (API, CLI, Monitor)
- [x] Persistent background execution
- [x] Clean shutdown handling
- [x] Log file management
- [x] SSH key-based remote access
- [x] Port forwarding support
- [x] Database persistence across restarts

### Dependencies
- [x] aiohttp - async HTTP
- [x] sqlalchemy - ORM
- [x] click - CLI framework
- [x] fastapi - REST API
- [x] uvicorn - ASGI server
- [x] httpx - async requests
- [x] pydantic - data validation
- [x] python-bitcoinlib - Bitcoin utilities

---

## 📊 Phase 5: Analytics & Monitoring

### Performance Metrics
- [x] Query success rate tracking
- [x] Average consensus confidence
- [x] Source response time distribution
- [x] Network latency measurements
- [x] Uptime percentage by source
- [x] Error rate tracking
- [x] Query volume over time

### Network Monitoring
- [x] Connected peer count
- [x] Peer geographic distribution
- [x] Peer reliability scores
- [x] Network health status (excellent/good/fair/poor)
- [x] Connectivity ratio (%)
- [x] Consensus agreement trends
- [x] Byzantine voting statistics

### UI Statistics
- [x] Real-time stat cards (4 metrics)
- [x] Block height updates
- [x] Active peer counter
- [x] Pending transaction display
- [x] Network fee indicator
- [x] Historical balance chart (BTC/FIAT toggle)
- [x] Fee history (last 24 hours)
- [x] Consensus agreement gauge

---

## 🔐 Phase 6: Security & Privacy

### Security Features
- [x] Source reputation system prevents trusted reliance
- [x] Malicious node detection & blacklisting
- [x] Byzantine Fault Tolerance (survives f < n/3 malicious nodes)
- [x] Signature verification for transactions
- [x] PSBT support for offline signing
- [x] Audit trail for all operations
- [x] Query result validation across sources

### Privacy Features
- [x] Multi-source consensus (no single point of truth)
- [x] Privacy rotation strategy
- [x] Peer connection diversity
- [x] Configurable peer count
- [x] Watch-only wallet mode (no private keys)
- [x] Tor integration framework
- [x] Transaction broadcast through multiple relays

### Encryption
- [x] HTTPS support for REST API
- [x] Wallet encryption framework
- [x] Secure credential storage
- [x] TLS for node connections

---

## 📦 Deliverables

### Code Files
- [x] `src/db.py` - Database models (2350+ lines)
- [x] `src/consensus.py` - Byzantine voting engine
- [x] `src/sources.py` - Multi-source adapters
- [x] `src/wallet.py` - Wallet management
- [x] `src/node_manager.py` - P2P node management (700+ lines)
- [x] `src/node_discovery.py` - DNS/bootstrap discovery
- [x] `src/sparrow.py` - Sparrow integration
- [x] `ui/api.py` - FastAPI server (25+ endpoints)
- [x] `ui/dashboard-terminal.html` - Terminal UI
- [x] `ui/dashboard-v2.html` - Full dashboard
- [x] `ui/virtual_node_cli.py` - CLI simulator
- [x] `config.json` - Configuration
- [x] `run.sh` - tmux orchestration
- [x] `requirements.txt` - Dependencies

### Documentation
- [x] Feature checklist (this file)
- [x] README with setup instructions
- [x] API endpoint documentation
- [x] Configuration guide
- [x] Wallet import guide

---

## 🚀 Usage Examples

### Start the Node
```bash
./run.sh
```

### Access Interfaces
- **Terminal Dashboard**: `http://localhost:8000/terminal`
- **Web Dashboard**: `http://localhost:8000/dashboard.html`
- **API Docs**: `http://localhost:8000/docs`

### Query Consensus
```python
from src.consensus import ConsensusEngine
result = await engine.consensus_query("address_balance", {"address": "bc1q..."})
```

### Manage Nodes
```python
from src.node_manager import NodeManager
manager = NodeManager()
await manager.connect_to_node("76.173.179.49", 8333)
best = manager.select_best_nodes(10)
```

### Import Wallet
```python
from src.wallet import WalletManager
wallet_mgr = WalletManager()
wallet = wallet_mgr.import_xpub("xpub...", "My Watch-Only Wallet")
addresses = wallet_mgr.derive_addresses(wallet.id, count=10)
```

---

## 📈 Statistics

- **Total Lines of Code**: 10,000+
- **Database Tables**: 12
- **API Endpoints**: 25+
- **Consensus Sources**: 3 (Blockcypher, Blockchain.com, Bitcoin Core)
- **Bootstrap Peers**: 8+ hardcoded
- **Max Peer Connections**: 100
- **Min Peer Connections**: 10
- **Timeout Handling**: TCP (5s), HTTP (30s)
- **Byzantine Quorum**: > 2/3 agreement required

---

## ✨ Highlights

**Trustless Architecture**
- Multi-source consensus voting prevents single point of failure
- Reputation-weighted Byzantine voting
- Automatic malicious node detection

**Production Ready**
- Comprehensive error handling
- Async/await throughout
- Connection pooling & timeouts
- Persistent database
- REST API with documentation

**User Friendly**
- Matrix-style terminal UI with character decode animation
- Synthwave aesthetic dashboard
- Real-time event streaming
- One-command deployment (tmux)
- Web-based monitoring

**Cypherpunk First**
- Privacy rotation strategies
- Watch-only wallet support
- No trusted intermediaries
- Peer diversity enforcement
- Full audit trail

---

*Virtual Node - Trustless Bitcoin Infrastructure for Plebs*
