# CryptoBhoomi — Blockchain-Based Land Registration System

A decentralized application (DApp) built on the Ethereum blockchain for secure, transparent, and tamper-proof land registration and ownership transfer.

## Features

- **MetaMask Wallet Authentication** — Users connect via Ethereum wallets
- **Land Registration** — Register property details & upload legal documents
- **Government Verification** — Revenue officers verify ownership on-chain
- **Property Marketplace** — List verified properties for sale
- **Purchase Requests & Negotiation** — Buyers send offers, sellers accept/reject
- **Ether Payment & Ownership Transfer** — Smart contract auto-transfers ownership
- **Admin Dashboard** — Manage users, officers, view reports & audit logs
- **Notification System** — Real-time activity notifications
- **Audit Trail** — Immutable log of all system activities
- **Transaction History** — Complete blockchain transaction records

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, JavaScript, Bootstrap 5 |
| Backend | Python Flask |
| Database | MongoDB |
| Blockchain | Solidity, Ethereum, Ganache, Truffle |
| Wallet | MetaMask |
| Web3 | Web3.js (frontend), Web3.py (backend) |

## Project Structure

```
Final_Project/
├── app.py                    # Main Flask server
├── config.json               # Configuration
├── requirements.txt          # Python dependencies
├── utils/
│   ├── blockchain.py         # Web3/blockchain helpers
│   └── db.py                 # MongoDB helpers
├── templates/
│   ├── base.html             # Master template
│   ├── app_layout.html       # App layout (sidebar)
│   ├── index.html            # Landing page
│   ├── about.html            # About page
│   ├── login.html            # Officer/Admin login
│   ├── register.html         # User registration
│   ├── properties.html       # Public property listing
│   ├── user/                 # User pages
│   ├── officer/              # Revenue officer pages
│   └── admin/                # Admin pages
├── static/
│   ├── css/style.css         # Design system
│   └── js/
│       ├── app.js            # Core JavaScript
│       └── web3.min.js       # Web3 library
├── uploads/                  # Document storage
└── Major-Project/            # Original project (backup)
    └── Smart_contracts/      # Solidity contracts & Truffle
```

## Installation & Setup

### Prerequisites
- Python 3.8+
- Node.js & npm
- [Ganache](https://trufflesuite.com/ganache/) — Local Ethereum blockchain
- [MetaMask](https://metamask.io/) — Browser extension
- [MongoDB](https://www.mongodb.com/try/download/community) — Database server
- Truffle — `npm install -g truffle`

### Step 1: Install Python Dependencies

```bash
cd Final_Project
python -m venv venv
# Windows:
venv\Scripts\activate
# Linux/Mac:
# source venv/bin/activate

pip install -r requirements.txt
```

### Step 2: Start MongoDB

Make sure MongoDB is running on `localhost:27017` (default).

### Step 3: Start Ganache

1. Open Ganache and create a new workspace
2. Note the RPC Server URL (default: `http://127.0.0.1:7545`)
3. Note the first account address (used for contract deployment)

### Step 4: Deploy Smart Contracts

```bash
cd Major-Project/Smart_contracts
truffle migrate --reset
```

Note the account used for deployment and update `config.json`:
```json
{
  "Address_Used_To_Deploy_Contract": "<YOUR_DEPLOYER_ADDRESS>"
}
```

### Step 5: Configure MetaMask

1. Open MetaMask in your browser
2. Add a custom network:
   - Network Name: Ganache
   - RPC URL: http://127.0.0.1:7545
   - Chain ID: 1337
   - Currency Symbol: ETH
3. Import Ganache accounts using private keys

### Step 6: Start the Application

```bash
cd Final_Project
python app.py
```

The server will start at **http://localhost:5000**

## Usage Workflow

1. **User** connects MetaMask wallet on the homepage
2. **User** registers with personal details (stored on blockchain)
3. **User** registers land with documents (property stored on blockchain, docs in MongoDB)
4. **Admin** logs in and adds a Revenue Officer
5. **Revenue Officer** logs in and verifies/rejects property registrations
6. **Seller** lists verified property for sale with asking price
7. **Buyer** browses available properties and sends purchase request
8. **Seller** reviews and accepts a buyer's offer
9. **Buyer** makes Ether payment through MetaMask
10. **Smart Contract** validates payment and auto-transfers ownership
11. All transactions are permanently recorded on the blockchain

## User Roles

| Role | Access |
|------|--------|
| **User (Seller/Buyer)** | Register land, list for sale, send purchase requests, make payments |
| **Revenue Officer** | Verify/reject property registrations |
| **Admin** | Manage officers, view all data, audit logs, reports |

## Configuration

Edit `config.json`:

```json
{
  "Ganache_Url": "http://127.0.0.1:7545",
  "NETWORK_CHAIN_ID": 5777,
  "Mongo_Db_Url": "mongodb://localhost:27017",
  "Secret_Key": "your_secret_key",
  "Address_Used_To_Deploy_Contract": "0x...",
  "Admin_Password": "12345678"
}
```

## Smart Contracts

| Contract | Purpose |
|----------|---------|
| `Users.sol` | User registration & identity management |
| `Properties.sol` | Land property data & state management |
| `LandRegistry.sol` | Ownership mapping & government verification |
| `TransferOfOwnership.sol` | Sales, bidding, payment & ownership transfer |

## Default Admin Login

- **Address**: The address used to deploy contracts
- **Password**: `12345678` (change in config.json)
