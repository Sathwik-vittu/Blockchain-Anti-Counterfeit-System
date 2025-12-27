# **Fake Product Detection System using Ethereum Blockchain**

A decentralized application (dApp) designed to eliminate counterfeit goods in the supply chain by leveraging the immutability of the Ethereum blockchain. This system allows manufacturers to register products, track ownership transfers through retailers, and enables end-consumers to verify authenticity via QR code scanning.

# 🏗 **System Architecture**

The project simulates a real-world supply chain with three primary stakeholders:
- **Manufacturer:** Registers a new product with a unique_id and product_name.
- **Retailer:** Receives ownership from the manufacturer, updating the product state on-chain.
- **Customer:** Scans the QR code to verify the entire "Chain of Custody" before purchase.

# 🛠 **Technical Stack**
- **Smart Contracts:** Solidity (^0.8.1) for core business logic and state management.
- **Blockchain Interaction:** Ethers.js for secure provider/signer communication with the Ethereum network.
- **Frontend:** Bootstrap 5 for a responsive dashboard and QR Code integration via html5-qrcode.
- **Wallet Integration:** MetaMask for transaction signing and identity verification.

# 🛡 Key Features
- **On-Chain Product Registration:** Manufacturers add products directly to the blockchain, creating an immutable record.
- **Ownership Tracking (SCD-style):** Every transfer of ownership is a verified transaction, preventing "Double-Spending" of product identities.
- **Instant Verification:** A scanning module that checks the all_product_details mapping and alerts users if a product is unmanufactured or already owned.
- **Permissioned Actions:** Uses the require(msg.sender == owner) pattern to ensure only authorized manufacturers can mint new product IDs.

# 📂 Code Highlights
- **fakeProduct.sol:** Contains the **owner_status** Enum (Manufacturer, Retailer, Customer) and the logic for state transitions during ownership transfer.
- **check.html:** Implements real-time blockchain querying. If a scanned ID returns **0x000...**, it triggers a "Never Manufactured" alert.
- **transfer.html:** Handles the logic for moving product IDs between cryptographic addresses.

# 🚀 How It Works
- **Deploy** the fakeProductDetection contract to an Ethereum testnet (e.g., Sepolia).
- **Connect** MetaMask to the application.
- **Generate** a QR code for a new Product ID.
- **Transfer** ownership to a Retailer's address.
- **Authenticate** as a customer by scanning the QR; the app confirms if the current owner matches the blockchain record.
